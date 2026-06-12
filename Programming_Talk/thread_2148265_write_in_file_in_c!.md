---
title: "write in file in c?!"
date: 2013-05-24
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-24
i want to write in a file, so i write code thats i think correct. but not works
```
logFileOpen = open(logFilePath, O_WRONLY);
    write(logFileOpen,handle,strlen(handle));
```

what is wrong?!

---

### Post by dargaud on 2013-05-24
you probably want fopen and fwrite instead of open and write.

---

### Post by nvteighen on 2013-05-24
What's the problem? Could you please send us the error and some more code?

And btw, we've told you already that you're better off using the higher-level C standard functions than using system calls.

---

### Post by ferizhandi on 2013-05-24
> **dargaud said:**
> you probably want fopen and fwrite instead of open and write.


i have to use system call function.

---

### Post by ferizhandi on 2013-05-24
> **nvteighen said:**
> What's the problem? Could you please send us the error and some more code?

And btw, we've told you already that you're better off using the higher-level C standard functions than using system calls.


my code is lengthful, but the part of code that relate with this case exist below:

```

logFileOpen=open(logFilePath,O_CREAT,0777);
close(logFileOpen);
```

and the other part:

```

logFileOpen = open(logFilePath, O_WRONLY); write(logFileOpen,handle,strlen(handle));
```

---

### Post by nvteighen on 2013-05-24
> **ferizhandi said:**
> i have to use system call function.

Why? Is this homework? Of course, there is nothing wrong with asking for **help** for your homework here (we won't do it for you, heh). However, you provide us too little information in your threads and this results in you getting an answer more slowly.

What we need to know in order to help you in a more efficient way:
1) More code. We need context in order to know if you're getting errors because of a variable that is declared in an incorrect type.
2) Output. We need to know what is your program doing.

Please, give us as much information as you can!

---

### Post by dwhitney67 on 2013-05-24
> **ferizhandi said:**
> i have to use system call function.

If open(), write(), read() are system call functions... then what classification do you apply to fopen(), fwrite(), and fread()?

---

### Post by lisati on 2013-05-24
As others have pointed out, we don't mind helping with homework, but won't do it for you.

I'd also suggest checking that opening the file actually worked before actually trying to write to it. If you don't, you could end up some weird and confusing output from your program if something goes wrong. 

It is possible that logFilePath doesn't have a suitable value, but we can't tell from the code snippets that have been provided.

---

### Post by ferizhandi on 2013-05-24
> **nvteighen said:**
> Why? Is this homework? Of course, there is nothing wrong with asking for **help** for your homework here (we won't do it for you, heh). However, you provide us too little information in your threads and this results in you getting an answer more slowly.

What we need to know in order to help you in a more efficient way:
1) More code. We need context in order to know if you're getting errors because of a variable that is declared in an incorrect type.
2) Output. We need to know what is your program doing.

Please, give us as much information as you can!

my homework is programmimg of  sever and client with many facilities. and in this part i want to save request of all client in log file. so at the first of sever code. i am open with O_CREAT then close it. and after that in one method i want to open it and write. but not perform.

my server code is below .(the colored part is my problem.some lines is in the first and one line at the end of code)

```

#include <string.h>
#include <stdio.h>
#include <stdlib.h>                // itoa();
#include <unistd.h>

#include <sys/socket.h>
#include <sys/types.h>
#include <sys/select.h>            // for select function. this function for know a client ready to recv , send data.
#include <arpa/inet.h>
#include <error.h>
#include <errno.h>

#include <fcntl.h>                //open file


#define TRUE 1
#define FALSE 0
#define MAX_USER 30
#define MAX_LENGTH_INSTRUCTION 30
#define NUMBER_OF_INSTRUCTION 9
#define MAX_CLIENT_MSG 100                        // baraye size bufferi ke baraye gereftan payame client ha tarif mikonim
int numberOfOnline=0;                            //number of person that conect to server now
const char* SERVER_NAME ="Esteghlal";            // server name
char  instruction_set[NUMBER_OF_INSTRUCTION][MAX_LENGTH_INSTRUCTION] = {"connect","get-clients-list","share","get-files-list","get","remove","rename","msg","dc"};
int   instruction_size[NUMBER_OF_INSTRUCTION]={7,16,5,14,3,6,6,3,2};

fd_set readfd;

typedef struct {
    int userIdNumber;
    char* userName;
    int isThere;

}client;
client clientList[MAX_USER];

char* dirpath="/home/freez/os-temp";

char* logFilePath;            //path of log file of server
int logFileOpen;

char* passFilePath;
int passFileOpen;


int runServer(char*, int);
void getClientList(int);
void serviceClient(int,char[]);                 //when receive a msg from client call this function for service to client;
void scanBuffer(char[],int);
void shareFile(char[],int);
void takeFileList(int);
int main(int argNum , char **args)
{


    int i;
    for(i=0;i<MAX_USER;i++)
    {
        clientList[i].userName=NULL;
        clientList[i].userIdNumber=-1;
        clientList[i].isThere=0;
    }

    if(argNum<3)
    {
        char  msg[] = "you should insert two argument: [path directory] [port number]\n";
        write(1, msg,sizeof(msg));
        return 0;
    }
    else
    {
        char* path = args[1];
        int portNumber=atoi(args[2]);
        int i;

        [I][B][COLOR=#ff0000]logFilePath=malloc((strlen(path)+4)*sizeof(char));
        strcat(logFilePath,dirpath);
        strcat(logFilePath,"/log");

        logFileOpen=open(logFilePath,O_CREAT,0777);
        close(logFileOpen);[/COLOR][/B][/I]


        passFilePath=malloc((strlen(path)+9)*sizeof(char));
        bzero(passFilePath,strlen(passFilePath));

        strcat(passFilePath,dirpath);
        strcat(passFilePath,"/password");

        passFileOpen=open(passFilePath,O_CREAT,0777);
        close(passFileOpen);






        if(portNumber<1024)                        //Port number less than 1024
        {
            char  msg[] = "the port number that u select not valid, you should choose more than 1024";
            write(1, msg,sizeof(msg));            // sizeof system call
            return 0;
        }
        else if(0)                                // directory not exist
        {
            return 0;
        }
        else
        {
            int run = runServer(path,portNumber);
            if(run==-1)
                return 0;

        }


    }
    return 0;
}
void takeFileList(int fd)
{
    int i;
    int which_client;
    for(i=0;i<MAX_USER;i++)
    {
        if(clientList[i].userIdNumber==fd)
            which_client=i;
    }
    char* handle=malloc((strlen(clientList[which_client].userName)+31)* sizeof(char));
    strcat(handle,"request to get the file list.\n");
    write(1,handle,strlen(handle));

    char* filepath=malloc((strlen(dirpath)+9)*sizeof(char));

    bzero(filepath,strlen(filepath));
    //strcat(filepath,dirpath);
    strcat(filepath,"fileList");
    int openfileList=open(filepath,O_RDONLY,0);
    char buffer[100];
    bzero(buffer,100);
    while(TRUE)
    {
        if(read(openfileList,buffer,100)>0)
        {
            write(1,buffer,strlen(buffer));
            send(fd,buffer,strlen(buffer),0);
        }
        else
        {
            int j;
            for(j=0;j<100;j++)
                buffer[j]='@';
            send(fd,buffer,strlen(buffer),0);
            break;
        }
        bzero(buffer,100);
    }
    return;
}
int runServer(char* pathDir, int portNum)
{
    int tcp_socket,maxSelect,activity,newSocket,addrsize;
    struct sockaddr_in server_addr;
    int server_addr_length;

    tcp_socket = socket(AF_INET,SOCK_STREAM,0); // IPV4 , TCP , IP
    if ( tcp_socket==-1 )
    {
        char handle_error[] = "socket not created so application terminate, please run again.";
        write(1,handle_error,strlen(handle_error));
        return -1;
    }
    int opt=TRUE;
    if(setsockopt(tcp_socket,SOL_SOCKET,SO_REUSEADDR,(char*)&opt,sizeof(opt))<0)
    {
        char handle_error ="ERROR: problem in set socket option occurred\n";
        write(1,handle_error,strlen(handle_error));
    }
    server_addr.sin_family = AF_INET;                // family address ipv4
    server_addr.sin_port= htons(portNum);                    // port number
    server_addr.sin_addr.s_addr = INADDR_ANY;        // recieve message from all address

    int mybind = bind(tcp_socket,(struct  sockaddr*)&server_addr,sizeof(server_addr));
    if(mybind==-1)
    {
        char handle_error[] = " ERROR in binding\n";
        write(1,handle_error,strlen(handle_error));
        return 0;
    }
    listen(tcp_socket,MAX_USER);
    while(TRUE)
    {
        FD_ZERO(&readfd);//clear the socket set
        FD_SET(tcp_socket,&readfd);//add socket
        maxSelect=tcp_socket;

        // add child socket
        int k;
        for(k=0;k<MAX_USER;k++)
        {

            if(clientList[k].isThere==1)
            {
                FD_SET(clientList[k].userIdNumber,&readfd);
                if(clientList[k].userIdNumber>maxSelect)
                    maxSelect=clientList[k].userIdNumber;
            }
        }
        activity= select(maxSelect+1,&readfd,NULL,NULL,NULL);

        if(FD_ISSET(tcp_socket,&readfd))                                //request for connecting
        {
            addrsize=sizeof(server_addr);
            newSocket = accept(tcp_socket,(struct sockaddr*)&server_addr,&addrsize);                //sizeof system call
            send(newSocket,"**************** WELCOME ******************\n",strlen("**************** WELCOME ******************\n"),0);
            int i,which;
            //******* set all struct client:
            for(i=0;i<MAX_USER;i++)
            {
                if(clientList[i].isThere==0)
                {
                    clientList[i].userIdNumber=newSocket;
                    clientList[i].isThere=1;
                    which=i;
                    i=MAX_USER;
                }
            }
            //-----------------------------
            //****** receive and detect name of client: ****

            char* newClientName=malloc(100*sizeof(char));
            while(1)
            {
                if(recv(newSocket,newClientName,100,0)>0)
                    break;
            }
            //write(1,newClientName,strlen(newClientName));
            int j=0;
            clientList[which].userName=malloc((strlen(newClientName)-1)*sizeof(char));
            for(j=0;j<100;j++)
            {
                if(newClientName[j]=='@')
                    break;
                clientList[which].userName[j]=newClientName[j];
            }
            //write(1,clientList[i].userName,strlen(clientList[i].userName));
            send(newSocket,SERVER_NAME,strlen(SERVER_NAME),0);
            write(1,clientList[which].userName,strlen(clientList[which].userName));
            write(1," connect to sever with IP : ",29);
            write(1,inet_ntoa(server_addr.sin_addr),strlen(inet_ntoa(server_addr.sin_addr)));
            write(1," and port is ",13);
            //int port=ntohs(server_addr.sin_port);
            //char* port1;
            //sprintf(port1,"%d",port);
            //write(1,,strlen(ntohs(server_addr.sin_port)));

            //write(1,port1,strlen(port1));
            write(1,"\n",1);
            numberOfOnline++;
        }
        int y;
        for(y=0;y<MAX_USER;y++)
        {
            if(clientList[y].isThere==1)
            {
                int socketNum=clientList[y].userIdNumber;
                if(FD_ISSET(socketNum,&readfd))
                {
                    int valRead;
                    char buffer[1024];
                    if((valRead=read(socketNum,buffer,1024))==0)        //request for close connection;
                    {
                        getpeername(socketNum,(struct sockaddr*)&server_addr,(socklen_t*)&addrsize);
                        write(1,"HOST Disconnect IP: ",20);
                        write(1,inet_ntoa(server_addr.sin_addr),strlen(inet_ntoa(server_addr.sin_addr)));
                        write(1,"  PORT: ",8);
                        //write(ntohs(server_addr.sin_port))
                        write(1,"\n",1);
                        close(socketNum);
                        clientList[y].isThere=0;
                        clientList[y].userIdNumber=-1;
                    }
                    else
                    {

                        scanBuffer(buffer,socketNum);
                    }
                }
            }
        }

    }

}
void scanBuffer(char buffer[],int socket)
{

    int wichInstruct;//which one of instruction_set
    int i;
    int instruct[2];// index of start and End of instruction
    int check=-1;
    for(i=0;i<strlen(buffer);i++)
    {
        if(buffer[i]!=' '&&check==-1)
        {
            instruct[0]=i;check=0;
        }
        if(check==0&&buffer[i]=='@')
            instruct[1]=i-1;
    }
    char* instruction=malloc(instruct[1]-instruct[0]+1);
    for(i=instruct[0];i<=instruct[1];i++)
    {
        instruction[i-instruct[0]]=buffer[i];
    }
    for(i=0;i<NUMBER_OF_INSTRUCTION;i++)
    {
        check=1;
        if(strlen(instruction)==instruction_size[i])
        {
            int j;
            for(j=0;j<instruction_size[i];j++)
            {
                if(instruction[j]!=instruction_set[i][j])
                    check=-1;
            }
        }
        else
            check=-1;
        if(check==1)
            break;
    }
    wichInstruct=i;
    /*write(1,"\n",1);
    write(1,"1234567890",wichInstruct);
    write(1,"\n",1);*/


    switch(wichInstruct){
    case 0:
            break;
    case 1:
            getClientList(socket);
            break;
    case 2:
            shareFile(buffer,socket);
            break;
    case 3:
            takeFileList(socket);
            break;
    case 4:
            break;
    case 5:
            break;
    case 6:
            break;
    case 7:
            break;
    case 8:
            break;
    case 9:
            break;
    default:
        break;
    }
}
void shareFile(char buffer[],int fd)
{
    int i=0;
    int which_client;
    char filename[100];
    bzero(filename,100);
    for(i=0;i<MAX_USER;i++)
    {
        if(clientList[i].userIdNumber==fd)
        {
            which_client=i;break;
        }
    }
    write(1,clientList[which_client].userName,strlen(clientList[which_client].userName));
    write(1," request to share file.\n",24);
    char* recvbuf=malloc(1000*sizeof(char));
    bzero(recvbuf,1000);
    while(TRUE)
    {
        if(recv(fd,filename,100,0)>0)
            break;
    }
    write(1,filename,strlen(filename));
    write(1,"\n",1);


    if(send(fd,"ok",2,0)>0)
    {
        int finish=0;
        char* end="finish@";

        while(TRUE)
        {
            bzero(recvbuf,1000);
            if(recv(fd,recvbuf,1000,0)>0)
            {
                finish=1;
                int j;
                for(j=0;j<1000;j++)
                {
                    if(recvbuf[j]!='@')
                    {
                        finish=0;
                    }
                }

                if(finish==1)
                {
                    //********* get password:
                    //write(1,"finish\n",7);
                    recv(fd,recvbuf,strlen(recvbuf),0);

                    break;
                }
                // ************* get content of file and save it:
                else
                {
                    write(1,recvbuf,strlen(recvbuf));
                }
            }
        }
    }
}
void getClientList(int fd)
{


    char number[5];

    bzero(number,strlen(number));

    int i;
    int which_client;
    for(i=0;i<MAX_USER;i++)
    {
        if(clientList[i].userIdNumber==fd)
        {    which_client=i;break;}
    }



    char *bufer=malloc(1000*sizeof(char));
    bzero(bufer,1000);

    int ptr=0;
    for(i=0;i<MAX_USER;i++)
    {
        if(clientList[i].isThere==1)
        {

            //bufer[ptr]='#';ptr++;bufer[ptr]='c';ptr++;bufer[ptr]='l';ptr++;bufer[ptr]='i';ptr++;
            strcat(bufer,"#cli");
            ptr=4;

            if(clientList[i].userIdNumber>99)
            {
                char number[3];
                sprintf(number,"%d",clientList[i].userIdNumber);
                int t;
                for(t=0;t<3;t++)
                {
                    bufer[ptr]=number[2-t];
                    ptr++;
                }
            }
            else if(clientList[i].userIdNumber>9)
            {
                char number[2];
                sprintf(number,"%d",clientList[i].userIdNumber);
                int t;
                for(t=0;t<2;t++)
                {
                    bufer[ptr]=number[1-t];
                    ptr++;
                }
            }
            else
            {
                char number[1];
                sprintf(number,"%d",clientList[i].userIdNumber);
                bufer[ptr]=number[0];
                ptr++;
            }
            bufer[ptr]=':';ptr++;
            strcat(bufer,clientList[i].userName);
            /*int k;
            for(k=0;k<strlen(clientList[i].userName);k++)
            {
                bufer[ptr]=clientList[i].userName[k];
                ptr++;
            }*/
            strcat(bufer,"\n");

        }
        int x;
        while(1)
        {
            if((x=send(fd,bufer,1000,0))>0)
            break;
        }
        bzero(bufer,1000);
        ptr=0;

    }

    char* msg="finish";
    while(1)
    {
        if((send(fd,msg,1000,0))>0)
        break;
    }
    char* handle=malloc((strlen(clientList[which_client].userName)+28)*sizeof(char));
    bzero(handle,strlen(handle));
    strcat(handle,clientList[which_client].userName);
    strcat(handle," request for Online client.\n");
    [COLOR=#ff0000]***logFileOpen = open("log", O_WRONLY);***[/COLOR]
    if(write(logFileOpen,handle,strlen(handle))==0)
    {
        write(1,"error",5);
    }
    write(1,handle,strlen(handle));
    //bzero(msg1,strlen(msg1));

}



```

---

