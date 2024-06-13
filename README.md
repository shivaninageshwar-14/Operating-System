# Operating-System
Shared Memory Code
  1 #include<stdio.h>
  2 #include<stdlib.h>
  3 #include<unistd.h>
  4 #include<string.h>
  5 #include<sys/shm.h>
  6 
  7 int main(){
  8     int shmid;
  9     char buff[7];
 10     void *sh;
 11     shmid = shmget((key_t)12345,1024,0666|IPC_CREAT);
 12     sh = shmat(shmid,NULL,0);
 13     read(0,buff,7);
 14     strcpy(sh,buff);
 15     printf("Data Received: %s\n",(char*)sh);
 16 }
 17 
