---
title: "A problem with c udp client/server"
date: 2008-11-20
forum: Programming Talk
---

### Post by MeLight on 2008-11-20
Hi all,
I have a problem with my homework (yes, my homework). The assignment is to write a UDP client/server to transfer files. The server must create a socket (with a port etc) and wait a until the client asks for a file. I've managed to create a server who waits (no errors there) and a client who supposetly writes to it's end socket, but the msg won't reach the server :(
here's my code so far:

server: (arguments: 20001  -s 22)
```

//-------- Includes
#include <stdio.h>
#include <stdlib.h>
#include <sys/socket.h> //for socket macros
#include <string.h>     //for memset
#include <netdb.h>      //for sizeof(servAddr)

//-------- Constants
#define MAX_MSG 512

//-------- Prototype
void checkAndSet(int paramNum, char** args, int *size, int *interval);
int checkNumOnly(char* value);
int checkNumAndOpt(char* value, char opt);
char checkParam(char* param);
void die(char *err_msg);

//----------------------------- Main
int main(int argc, char** argv) {
    int port;
    int size = -1;
    int interval = -1;
    int ssocket;       //server socket and client socket
    struct sockaddr_in serv, clnt;    //server and client address structs
    char msg[MAX_MSG];
    
    //--------------------- Checking parameters
    if(argc != 2 && argc != 4 && argc != 6) {
        fprintf(stderr, "usage: ftserver <local port> [-s  < msg_size>] [-i < interval>l]\n");
        exit(1);
    }
    
    else if(argc >= 2) {
        if(!checkNumOnly(argv[1]) || (port = atoi(argv[1])) > 65535) {
            fprintf(stderr, "Invalid port parameter %s\n", argv[1]);
            exit(1);
        }
        
        port = htons(atoi(argv[1]));
        
        if(argc >= 4) {        
            checkAndSet(2, argv, &size, &interval);

            if(argc == 6) {
                checkAndSet(4, argv, &size, &interval);
            }
        }
        
        if(size == -1) size = 1400;
        if(interval == -1) interval = 1;
    }
    
    printf("Port: %d, size: %db, interval %dms\n", port, size, interval);   //remove after debug
    //--------------------- End of checking parameters
    
    
    if((ssocket = socket(PF_INET, SOCK_DGRAM, 0)) < 0) {
        die("Failed to create socket");
    }
    
    memset(&serv, 0, sizeof(serv));     //nullify the serv struct
    serv.sin_family = AF_INET;
    serv.sin_addr.s_addr = htonl(INADDR_ANY);
    serv.sin_port = htons(port);
    
    if(bind(ssocket, (struct sockaddr*) &serv, sizeof(serv)) < 0) {
        die("Failed to bind server to socket socket");
        exit(1);
    }
    struct sockaddr_in address;
    
    //Something's not working here i think
    while(1) {
        int clntLen = sizeof(clnt);
        printf("blah \n");
        /*int nbytes = recvfrom(ssocket, msg, 2, 0, 
                (struct sockaddr*) &clnt, &clntLen);*/
        read(ssocket, msg, 30);
        
        printf("Msg: %s\n", msg);
    }    
    close(ssocket);
    return (EXIT_SUCCESS);
}
//------------------------ Functions
//check and set param <num>
void checkAndSet(int paramNum, char** args, int *size, int *interval) {
    char p;
    if(!(p = checkParam(args[paramNum]))) {
        fprintf(stderr, "Invalid parameter %s\n", args[paramNum]);
        exit(1);
    }

    if(p == 's') {
        if(!checkNumOnly(args[paramNum + 1]) || atoi(args[paramNum + 1]) > 65536) {
            fprintf(stderr, "Invalid size parameter %s\n", args[paramNum + 1]);
            exit(1);
        }            
        *size = atoi(args[paramNum + 1]);
    }
    else if(p == 'i') {
        if(!checkNumAndOpt(args[paramNum + 1], '.')) {
            fprintf(stderr, "Invalid interval parameter %s\n", args[paramNum + 1]);
            exit(1);
        }

        *interval = (int)(1000 * atof(args[3]));
    }
    else {
        fprintf(stderr, "Invalid parameter %s\n", args[paramNum]);
        exit(1);
    }
}

//check the letter of the param and return it
char checkParam(char* param) {
    if(strlen(param) != 2) return 0;
    if(param[0] != '-') return 0;
    return param[1];
}

//checks if the string contains numbers only
int checkNumOnly(char* value) {
    int len = strlen(value);
    int i = 0;
    for(i = 0; i < len; i++) {
        if(!isdigit(value[i])) return 0;
    }
    
    return 1;
}
//checks if the string contains only numbers and optional value
int checkNumAndOpt(char* value, char opt) {
    int len = strlen(value);
    int i = 0;
    for(i = 0; i < len; i++) {
        if(!isdigit(value[i]) && value[i] != opt) return 0;
    }
    
    return 1;
}

void die(char *msg) {
    perror(msg);
    exit(1);
}
```

client: (arguments: localhost 20001 blah /home/yuri/Desktop/testing.txt)

```
//-------- Includes
#include <stdio.h>
#include <stdlib.h>
#include <netinet/in.h>
#include <netdb.h>      //for sizeof(servAddr)
#include <string.h>     //for memset
#include <fcntl.h>      //for open() flags consts
#include <sys/stat.h>   //for open() mode consts
//#include <sys/types.h>

//-------- Constants

//-------- Prototype
int checkNumOnly(char* value);
void die(char *msg);


//----------------------------- Main
int main(int argc, char** argv) {
    struct sockaddr_in serv;    //server address struct
    struct hostent *hent;       //used for retrieving the server address
    int port;                   //server port
    int sock;
    char *reqfile, *localfile;  //the files to request and to save locally
    int fd;                     //file descriptor of teh open file
    
    
    //------------- Checking arguments
    if(argc != 5) 
    {
        fprintf(stderr, "usage: ftclient <server host> <sever port> <file to fetch> <save locally as>\n");
        exit(1);
    }
    
    //checking server address
    if((hent = gethostbyname(argv[1])) == NULL) {
        fprintf(stderr, "Invalid host %s\n", argv[1]);
        exit(1);
    }
    
    //checking port
    if(!checkNumOnly(argv[2]) || (port = atoi(argv[1])) > 65535) {
        fprintf(stderr, "Invalid port parameter %s\n", argv[2]);
        exit(1);
    }        
    port = atoi(argv[2]);
    
    reqfile = argv[3];
    localfile = argv[4];
    
    //------------- End of checking arguments
    
    //putting the server address in the struct
    memset(&serv, 0, sizeof(serv));
    serv.sin_family = AF_INET;
    memcpy((char*)&serv.sin_addr.s_addr, hent->h_addr, hent->h_length);
    serv.sin_port = htons(port);
    
    //opening socket
    if((sock = socket(PF_INET, SOCK_DGRAM, 0)) < 0) {
        die("Failed to create socket");
    }
    
    
    //opening the file we want to write to:
    /*if((fd = open(localfile, O_RDWR | O_EXCL | O_CREAT, S_IRWXU)) < 0) {
        die("Can not open file");
    }*/
    
    if(connect(sock, (struct sockaddr*) &serv, sizeof(serv)) < 0) {
        die("Could not connect to server");
    }
    
    //The msg from here doesnt want to get through :((
    char *msg = "aabbcc";
    write(sock, msg, sizeof(msg));

    //clean after debug
    char *ip = inet_ntoa(serv.sin_addr);
    printf("IP: %s, localfile: %s, port: %d\n", ip, localfile, serv.sin_port);
    close(sock);
    return (EXIT_SUCCESS);
}

//------------------- Functions ----------------

//checks if the string contains numbers only
int checkNumOnly(char* value) {
    int len = strlen(value);
    int i = 0;
    for(i = 0; i < len; i++) {
        if(!isdigit(value[i])) return 0;
    }
    
    return 1;
}

//die with error
void die(char *msg) {
    perror(msg);
    exit(1);
}
```

I run both, client and server on the same machine, which is on a wireless network (is that a problem??)
Any help is appreciated, thanx

---

