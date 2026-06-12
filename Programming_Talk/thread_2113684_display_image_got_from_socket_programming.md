---
title: "display image got from socket programming"
date: 2013-02-08
forum: Programming Talk
---

### Post by sanda199 on 2013-02-08
Hi everyone, I wrote client/server socket programming in c language to send image over. And my program can receive image and save it somewhere else. But now I wanna appear image as soon as I receive. I think I need to use gui. So I use Qt gui. But I don't know how to link with my gui and my socket programming. If anyone knows, pls kindly show me a way to do it. Thanks a lot. :)

Client.c 

```

#include <netdb.h>
#include <netinet/in.h>
#include <string.h>
#include <stdio.h>

int fileSEND(char *server, int PORT, char *lfile, char *rfile)
{
    int socketDESC;
    struct sockaddr_in serverADDRESS;
    struct hostent *hostINFO;
    FILE *file_to_send;
    int ch;
    char toSEND[1];
    char remoteFILE[4096];
    int count1=1, count2=1, percent;
    
    hostINFO = gethostbyname(server);
    if(hostINFO==NULL)
    {
        printf("Problem interpreting host\n");    
        return 1;
    }

    socketDESC = socket(AF_INET, SOCK_STREAM, 0);
    if(socketDESC<0)
    {
        printf("Cannot create socket\n");
        return 1;
    }
    
    serverADDRESS.sin_family = hostINFO->h_addrtype;
    memcpy((char *) &serverADDRESS.sin_addr.s_addr, hostINFO->h_addr_list[0],hostINFO->h_length);
    serverADDRESS.sin_port = htons(PORT);
    
    if(connect(socketDESC,(struct sockaddr *)&serverADDRESS,sizeof(serverADDRESS))<0)
    {
        printf("Cannot connect\n");
        return 1;
    }
    
    file_to_send = fopen(lfile, "r");
    if(!file_to_send)
    {
        printf("Error opening file\n");
        close(socketDESC);
        return 0;
    }
    else
    {
        long fileSIZE;
        fseek(file_to_send,0,SEEK_END);
        fileSIZE=ftell(file_to_send);
        rewind(file_to_send);
        
        sprintf(remoteFILE,"FBEGIN:%s:%ld\r\n",rfile,fileSIZE);
        send(socketDESC,remoteFILE,sizeof(remoteFILE),0);
        percent = fileSIZE/100;
        while((ch=getc(file_to_send))!=EOF)
        {
            toSEND[0]=ch;
            send(socketDESC,toSEND,1,0);
            if(count1==count2)
            {
                printf("33[0;0H"); 
                printf("\33[2J");
                printf("Filename: %s\n",lfile);
                printf("Filesize: %ld Kb\n", fileSIZE/1024);
                printf("Percent: %d%% (%d Kb)\n", count1/percent,count1/1024);
                count1+=percent;
            }
            count2++;
        }
    }
    fclose(file_to_send);
    close(socketDESC);
    return 0;
}

int main()
{
    fileSEND("localhost", 4547, "1.jpeg", "received.jpeg");
    return 0;
}

```


server.c 

```

#include <netdb.h>
#include <netinet/in.h>
#include <string.h>
#include <stdio.h>

#define PORT 4547

int parseARGS(char **args, char *line)
{
    int tmp = 0;
    args[tmp] = strtok(line, ":" );
    while ((args[++tmp] = strtok(NULL, ":" )) != NULL);
    return tmp -1;
}

int main()
{
    char *header[4096];
    int listenSOCKET, connectSOCKET;
    socklen_t clientADDRESSLENGTH;
    struct sockaddr_in clientADDRESS, serverADDRESS;
    char recvBUFF[4096];
    char *filename, *filesize;
    FILE *recvFILE;
    int received = 0;
    char tempstr[4096];
    
    int count1=1, count2=1, percent;
    
    listenSOCKET = socket(AF_INET, SOCK_STREAM, 0);
    if (listenSOCKET <0)
    {
        printf("Cannot create socket\n");
        close(listenSOCKET);
        return 1;
    }
    
    serverADDRESS.sin_family = AF_INET;
    serverADDRESS.sin_addr.s_addr = htonl(INADDR_ANY);
    serverADDRESS.sin_port = htons(PORT);

    if (bind(listenSOCKET, (struct sockaddr *)&serverADDRESS, sizeof(serverADDRESS))<0)
    {
        printf("Cannot bind socket\n");
        close(listenSOCKET);
        return 1;
    }
    
    listen(listenSOCKET, 5);
    clientADDRESSLENGTH = sizeof(clientADDRESS);
    connectSOCKET = accept(listenSOCKET,(struct sockaddr *)&clientADDRESS, &clientADDRESSLENGTH);
    if (connectSOCKET<0)
    {
        printf("Cannot accpet connection\n");
        close(listenSOCKET);
        return 1;
    }
    
    while(1)
    {
        if(recv(connectSOCKET, recvBUFF, sizeof(recvBUFF),0))
        {
            if(!strncmp(recvBUFF,"FBEGIN",6))
            {
            recvBUFF[strlen(recvBUFF)-2] = 0;
            parseARGS(header, recvBUFF);
            filename = header[1];
            filesize = header[2];
            }
        recvBUFF[0] = 0;
        recvFILE = fopen(filename, "w");
        percent = atoi(filesize)/100;
        printf("Current percent value: %d\n",percent);
        while(1)
        {
            if(recv(connectSOCKET,recvBUFF,1,0) != 0)
            {
                fwrite(recvBUFF,sizeof(recvBUFF[0]),1,recvFILE);
                if(count1==count2)
                {
                    printf("33[0;0H"); 
                    printf("\33[2J");
                    printf("Filename: %s\n", filename);
                    printf("Filesize: %d Kb\n", atoi(filesize)/1024);
                    printf("Percent: %d%% (%d Kb)\n", count1/percent,count1/1024);
                    count1+=percent;
                    printf("Show count1 value: %d\n",count1);
                }
                count2++;
                printf("Show count2 value: %d\n", count2);
                received++;
                recvBUFF[0] = 0;
            }
            else 
            {
                close(listenSOCKET);
                return 0;
            }
        }
        close(listenSOCKET);
        }
    else
    {
        printf("Client dropped connection\n");
    }
    return 0;
    }
}


```



myqtgui program

```

#include <QtGui/QApplication>
#include "mainwindow.h"
#include <QLabel>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    QImage myImage;

    myImage.load("/home/sanda199/programs/received.jpeg");

    QLabel myLabel;
    myLabel.setPixmap(QPixmap::fromImage(myImage));

    myLabel.show();

    return a.exec();
}

```


Thanks again.

---

### Post by Tony Flury on 2013-02-08
> **sanda199 said:**
> Hi everyone, I wrote client/server socket programming in c language to send image over. And my program can receive image and save it somewhere else. But now I wanna appear image as soon as I receive. I think I need to use gui. So I use Qt gui. But I don't know how to link with my gui and my socket programming. If anyone knows, pls kindly show me a way to do it. Thanks a lot. :)

... code snipped ...

Thanks again.

At least three ways :
1) Use a system call to invoke a built in viewer - i.e. you don't need to write your own image viewer - on Gnome the viewer is called eog.
2) Use a system call to invoke your viewer - you will probably want to adapt your viewer so it takes command line argument of the file you want to view.
3) Make your viewer code a callable function - and call it from your receiving code, and then link the two modules together.

---

### Post by sanda199 on 2013-02-09
> **Tony Flury said:**
> At least three ways :
1) Use a system call to invoke a built in viewer - i.e. you don't need to write your own image viewer - on Gnome the viewer is called eog.
2) Use a system call to invoke your viewer - you will probably want to adapt your viewer so it takes command line argument of the file you want to view.
3) Make your viewer code a callable function - and call it from your receiving code, and then link the two modules together.



Hi at first, thanks for your answer. As you suggest, I wanna use 3rd method. But you said make your viewer code a callable function means I have to make my gui code to be a callable function right. If so, how to do for it? I am a bit confused and not familiar with Qt.

---

### Post by sanda199 on 2013-02-09
Is it possible to run Qt program from my socket program in c language?

---

### Post by Tony Flury on 2013-02-09
> **sanda199 said:**
> Hi at first, thanks for your answer. As you suggest, I wanna use 3rd method. But you said make your viewer code a callable function means I have to make my gui code to be a callable function right. If so, how to do for it? I am a bit confused and not familiar with Qt.

Ok in your qt program, instead of a main function call it something like displayImage()

In your server code call displayImage as appropriate when you have received the file. 

Then you need to compile them together. 

gcc server.c myqtguic.c -o server 

This command compiles both c files and passes them to a linker to stitch them together. 

This should work. I can't test it  and you may need some extra options. 

Your server application should be executable as .//server.

---

