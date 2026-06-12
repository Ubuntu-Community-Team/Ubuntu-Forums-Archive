---
title: "How to find default system proxy settings in UBUNTU"
date: 2011-08-28
forum: Programming Talk
---

### Post by @TAN on 2011-08-28
I am trying to write a program which will read GET request from web browser analyze/edit it, then redirect it to the proxy server. I am finished with the GET request part, but I am unable to find proxy servers ip address or port to create a socket. can anyone tell me how to find the default proxy settings in ubuntu. please help

---

### Post by @TAN on 2011-08-28
This is my code. I have used some proxy servers ip and port found from google, but it doesn't work. I am using C by the way.


#include    "cc352.h" 
#include <arpa/inet.h> 
#include <string.h> 
#include <stdlib.h> 
#include <stdio.h> 
 
int 
main(int argc, char **argv) 
{ 
    int            listenfd, connfd,weblin,webcon,webwrite,n,x,y; 
    socklen_t        len,wlen; 
    struct sockaddr_in    servaddr, cliaddr , webservad , webcliad; 
    char            buff[3072] , buff2[3072] , buff3[1000], ext[5] , wbuff[3072]; 
    time_t            ticks; 
    int yes = 1; 
    const char    *ptr; 
 
    if ( (listenfd = socket(AF_INET, SOCK_STREAM, 0)) < 0 ){ 
        fprintf(stderr, "socket creation failed\n"); 
        exit (1); 
    } 
 
    bzero(&servaddr, sizeof(servaddr)); 
    servaddr.sin_family      = AF_INET; 
    if (inet_pton(AF_INET,"127.0.0.1", &servaddr.sin_addr) <= 0){ 
        printf("inet_pton error for %s", argv[1]); 
        return 1; 
    } 
    servaddr.sin_port        = htons(4615); /* daytime server */ 
 
    if ( (bind(listenfd, (SA *) &servaddr, sizeof(servaddr))) < 0) { 
        fprintf(stderr, "bind failed\n"); 
        exit (1); 
        fprintf(stderr, "binded\n"); 
    } 
 
     
//========================================================================================= 
    if ( (weblin = socket(AF_INET, SOCK_STREAM, 0)) < 0 ){ 
        fprintf(stderr, "socket creation failed\n"); 
        exit (1); 
    } 
     
    bzero(&servaddr, sizeof(webservad)); 
    servaddr.sin_family      = AF_INET; 
    if (inet_pton(AF_INET,"123.30.185.86", &webservad.sin_addr) <= 0){ 
        printf("inet_pton error for %s", argv[1]); 
        return 1; 
    } 
    webservad.sin_port        = htons(3128); /* daytime server */ 
 
     
 
     
     
    if (connect(weblin, (SA *) &webservad, sizeof(webservad)) < 0) { 
        printf("connect error2"); 
        return 1;  
    } 
//========================================================================================= 
    if ( listen(listenfd, LISTENQ) < 0) { 
        fprintf(stderr, "listen failed\n"); 
        exit (1); 
        fprintf(stderr, "listning\n"); 
    } 
     
 
    //for ( ; ; ) { 
        len = sizeof(cliaddr); 
        if ( (connfd = accept(listenfd, (SA *) &cliaddr, &len)) < 0 ) { 
            fprintf(stderr, "accept failed\n"); 
            exit (1); 
        } 
        fprintf(stdout, "Connection accepted\n"); 
    //} 
             
 
    for(;;){ 
    read(connfd,(char *) &buff,3071); 
        printf("Reading buffer\n"); 
        for(x=4 ; x<3072 ; x++){ 
            buff2[x-4]=buff[x]; 
        } 
        //printf(buff); 
        printf("Request captured \n %s \n",strtok(buff2," ")); 
        y=strlen(buff2); 
        ext[0]=buff2[y-4]; 
        ext[1]=buff2[y-3]; 
        ext[2]=buff2[y-2]; 
        ext[3]=buff2[y-1]; 
        ext[4]=buff2[y]; 
        printf("extention:%s \n",ext); 
        FILE *fp; 
        fp=fopen("location.txt","a"); 
        fprintf(fp,buff2); 
        fprintf(fp," "); 
        fprintf(fp,ext); 
        fprintf(fp,"\n"); 
        fclose(fp); 
         
        //if (fputs(buff, stdout) == EOF) { 
            //printf("fputs error"); 
            //printf("closing \n"); 
            //printf("[%s] \n",buff); 
            //return 1; 
         
    //} 
//} 
 
    if (n < 0) { 
        printf("read error"); 
        return 1; 
    } 
     
 
//========================================================================================= 
     
 
    if ( write(weblin, buff, strlen(buff)) != strlen(buff)) { 
        fprintf(stderr, "accept failed\n"); 
        exit (1); 
    } 
 
     
 
    while ( (n = read(weblin, wbuff, MAXLINE)) > 0) { 
        wbuff[n] = 0;    /* null terminate */ 
        } 
         
         
 
 
    if ( write(connfd, wbuff, strlen(wbuff)) != strlen(wbuff)) { 
        fprintf(stderr, "accept failed\n"); 
        exit (1); 
    } 
} 
     
//========================================================================================= 
 
        if ( close(connfd) == -1) { 
            fprintf(stderr, "accept failed\n"); 
            exit (1); 
        } 
    close(webcon); 
    close(weblin); 
    close(listenfd); 
return 0; 
    }

---

