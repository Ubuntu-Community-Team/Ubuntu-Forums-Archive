---
title: "Blocked by serial port programing"
date: 2012-04-13
forum: Programming Talk
---

### Post by pellyhawk on 2012-04-13
I am working on a serial port related project and block by serial port communication in the code in red(dc.c). 

Any help? Thanks

dc.c
```
#include <stdio.h>
#include <sys/socket.h>       /*  socket definitions        */
#include <sys/types.h>        /*  socket types              */
#include <arpa/inet.h>        /*  inet (3) funtions         */
#include <DcSerialPort.h>
//#include <DcSocket.h>
#include <constant.h>

extern cliCmd cliCmdsList[ ];

int main(int argc, char **argv)
{
   int *serialfd;
   int *clisock = NULL;
   int *appsock = NULL;
   int *mngsock = NULL;

   char *szDcIp = NULL;
   char *szDcPort = NULL;
   char *endPtr;
   struct sockaddr_in servAddr;

   char type;
   short length;

   int i;
   int readnum;
   printf("Start up!!\n");
   unsigned char *input_p = userInputBuff;

   //open serial port
   serialstarting(COM4, serialfd);
   printf("Serial port initialization has been completed!\n");

   szDcIp = "192.168.1.8";
   //start sockets
   //socketstarting(szDcIp, PRIME_DC_DFLT_CLI_PORT, clisock);
   //socketstarting(szDcIp, PRIME_DC_DFLT_APP_PORT, appsock);
   //socketstarting(szDcIp, PRIME_DC_DFLT_MNG_PORT, mngsock);
   //printf("Sockets have been built!\n");

   while (1)
   {
       int rc;
       unsigned char *input_p = userInputBuff;

       sleep(1);

[COLOR="Red"]       printf(">> ");
       memset(&userInputBuff, 0, MAX_BUFF_BYTES);
       readnum = read(serialfd,userInputBuff,MAX_BUFF_BYTES);[/COLOR]

       printf("read %d bytes from serial port\n", readnum);

       if (readnum <= 0)
       {
           continue;
       }

       type = *input_p;
       if ((type >= 0x10) && (type <= 0x21))
       {
           length = *(input_p +2 ) || (*(input_p + 3) >> 8);
           write(serialfd, input_p, length);
           if (trace_flag)
           {
               for (i = 0; i < length; i++)
               {
                   printf("%02x ", input_p[i]);
               }
               printf("\n");
           }
       }
       else if ((type >= 0x40) && (type <= 0x74))
            {
                length = *(input_p +2 ) || (*(input_p + 3) >> 8);
                write(serialfd, input_p, length);
                if (trace_flag)
                {
                   for (i = 0; i < length; i++)
                   {
                       printf("%02x ", input_p[i]);
                   }
                   printf("\n");
                }
            }

       while (*input_p == ' '
              || *input_p == '\t')
       {
           input_p++;
       }

       if (input_p[0] == '\0')
       {
           printf(">>%s\n", lastUserInputBuff);
           strcpy(input_p, lastUserInputBuff);
       }
       else
       {
           strcpy(lastUserInputBuff, input_p);
       }

       if (input_p[0] == 'q' || input_p[0] == 'Q')
           break;

       if (input_p[0] == '?')
       {
           int idx = 0;
           while (cliCmdsList[idx].cmdStr != NULL)
           {
                  printf("%s\n", cliCmdsList[idx].cmdStr);
                  idx ++;
           }
           printf("\n");
           continue;
       }
       else {
                printf("Message type Error!\n");
                if (trace_flag)
                {
                   for (i = 0; i < MAX_BUFF_BYTES; i++)
                   {
                       printf("%02x ", input_p[i]);
                   }
                   printf("\n");
                }
                continue;
            }
   }

   //close serial port and sockets
   close(*serialfd);
   close(*clisock);
   close(*appsock);
   close(*mngsock);

   return 0;
}
```
DcSerialPort.h
```
int set_opt(int fd, int nSpeed, int nBits, char nEvent, int nStop);
int open_port(int fd, int comport);
int serialstarting(int serialport, int *serialID);
```

DcSerialPort.c
```
#include <stdio.h>
#include <string.h>
#include <sys/types.h>
#include <errno.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <termios.h>
#include <stdlib.h>
#include <DcSerialPort.h>


#if 0
int main(void)
{
    int fd;
    int nread , nwrite;
    int i;
    char buff[8];
    fd_set rd;

    if((fd = open_port(fd,1)) < 0)
    {
        perror("open_port error");
        return ;
    }

    if((i = set_opt(fd,115200,8,'N',1)) < 0)
    {
        perror("set_opt error");
        return ;
    }

    FD_ZERO(&rd);
    FD_SET(fd,&rd);
    while(FD_ISSET(fd,&rd))
    {
        if(select(fd+1,&rd,NULL,NULL,NULL) < 0){
        perror("select");
    }
        else{
            while((nread = read(fd,buff,8)) > 0)
        {
            printf("nread=%d,%s/n",nread,buff);
        }
        }
    }
    close(fd);
    return ;
}
#endif

int set_opt(int fd, int nSpeed, int nBits, char nEvent, int nStop)
{
    struct termios newtio;
    struct termios oldtio;

    if(tcgetattr(fd,&oldtio) != 0)
    {
        perror("SetupSerial 1");
        return -1;
    }

    bzero(&newtio,sizeof(newtio));
    newtio.c_cflag |= CLOCAL |CREAD;
    newtio.c_cflag &= ~CSIZE;

    switch(nBits)
    {
        case 7:
            newtio.c_cflag |= CS7;
        break;
        case 8:
        newtio.c_cflag |= CS8;
        break;
    }

    switch(nEvent)
    {
        case 'O':
            newtio.c_cflag |= PARENB;
        newtio.c_cflag |= PARODD;
        newtio.c_iflag |= (INPCK | ISTRIP);
            break;
        case 'E':
        newtio.c_iflag |= (INPCK |ISTRIP);
        newtio.c_cflag |= PARENB;
        newtio.c_cflag &= ~PARODD;
        break;
    case 'N':
        newtio.c_cflag &= ~PARENB;
        break;
    }

    switch(nSpeed)
    {
        case 2400:
        cfsetispeed(&newtio,B2400);
        cfsetospeed(&newtio,B2400);
            break;
    case 4800:
        cfsetispeed(&newtio,B4800);
        cfsetospeed(&newtio,B4800);
        break;
    case 9600:
        cfsetispeed(&newtio,B9600);
        cfsetospeed(&newtio,B9600);
        break;
    case 115200:
        cfsetispeed(&newtio,B115200);
        cfsetospeed(&newtio,B115200);
        break;
    case 460800:
        cfsetispeed(&newtio,B460800);
        cfsetospeed(&newtio,B460800);
        break;
    default:
            cfsetispeed(&newtio,B9600);
            cfsetospeed(&newtio,B9600);
            break;
    }

    if(nStop == 1){
        newtio.c_cflag &= ~CSTOPB;
    }
    else if(nStop ==2){
        newtio.c_cflag |= CSTOPB;
    }
    newtio.c_cc[VTIME] = 0;
    newtio.c_cc[VMIN] = 0;

    tcflush(fd,TCIFLUSH);
    if((tcsetattr(fd,TCSANOW,&newtio)) != 0)
    {
        perror("com set error");
        return -1;
    }
    printf("Serial port is Set successfully!\n");
    return 0;
}

int open_port(int fd,int comport)
{
    char *dev[]={"/dev/ttyS0","/dev/ttyS1","/dev/ttyS2","/dev/ttyS3"};
    long vdisable;
    if(comport == 1)
    {
        fd = open("/dev/ttyS0",O_RDWR|O_NOCTTY|O_NDELAY);
    if(fd == -1){
        perror("Can't Open Serial Port COM1/ttyS0");
        return -1;
        }
    }

    else if(comport == 2)
    {
        fd = open("/dev/ttyS1",O_RDWR|O_NOCTTY|O_NDELAY);
        if(fd == -1){
            perror("Can't Open Serial Port COM2/ttyS1");
            return -1;
        }
    }

    else if(comport == 3)
    {
        fd = open("/dev/ttyS2",O_RDWR|O_NOCTTY|O_NDELAY);
        if(fd == -1){
            perror("Can't Open Serial Port COM3/ttyS2");
            return -1;
        }
    }
    else if(comport == 4)
    {
        fd = open("/dev/ttyS3",O_RDWR|O_NOCTTY|O_NDELAY);
        if(fd == -1){
            perror("Can't Open Serial Port COM4/ttyS3");
            return -1;
        }
    }
#if 0
    if(fcntl(fd,F_SETFL,0) < 0){
    printf("fcntl failed\n");
    }
    else{
    printf("fcntl=%d\n",fcntl(fd,F_SETFL,0));
    }

    if(isatty(STDIN_FILENO) == 0){
    printf("standard input is not a terminal device/n");
    }
    else{
        printf("isatty sucess!\n");
    }

    printf("fd-open=%d/n",fd);
#endif
    printf("Open serial port COM%d/ttyS%d successfully!\n", comport, comport-1);
    return fd;
}

int serialstarting(int serialport, int *serialID)
{
    int fd;
    int nread;
    int i;
    //char buff[];

    if((fd = open_port(fd,serialport)) < 0)
    {
        perror("open_port error");
        return ;
    }

    serialID = &fd;

    if((i = set_opt(fd,115200,8,'N',1)) < 0)
    {
        perror("set_opt error");
        return ;
    }

    //printf("fd=%d\n",fd);
    //nread = read(fd,buff,8);
    //printf("nread=%d\n",nread);

    return ;
}

```

constant.h
```
#define COM1 1
#define COM2 2
#define COM3 3
#define COM4 4

#define MAX_BUFF_BYTES 1024

char userInputBuff[MAX_BUFF_BYTES];
char lastUserInputBuff[MAX_BUFF_BYTES] = "\n";

#if 1
int trace_flag = 1;
#endif


#define PRIME_DC_DFLT_CLI_PORT  10000
#define PRIME_DC_DFLT_APP_PORT  20000
#define PRIME_DC_DFLT_MNG_PORT  50000

```

---

