---
title: "Socket programming, server resets connection"
date: 2009-01-29
forum: Programming Talk
---

### Post by Adntu on 2009-01-29
hi
I am trying to control a PTZ Camera via its web interface (web server), I create a socket and send the first command, the Camera moves, but when I send the second command the web server resets[RST] the connection (I use Wireshark/Ethereal to look into the packets), here is my c++ code:
[PHP]```

#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <netdb.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include<iostream>

int main(){

        int sock;
        const char* send_data;
        struct hostent *host;
        struct sockaddr_in server_addr;
        host = gethostbyname("168.144.18.31");

        if ((sock = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
            perror("Socket Error");
            exit(1);
        }

        server_addr.sin_family = AF_INET;
        server_addr.sin_port = htons(80);
        server_addr.sin_addr = *((struct in_addr *)host->h_addr);
        bzero(&(server_addr.sin_zero),8);

        if (connect(sock, (struct sockaddr *)&server_addr,
                    sizeof(struct sockaddr)) == -1)
        {
            perror("Connect");
            exit(1);
        }

        send_data="GET /axis-cgi/com/ptz.cgi?camera=1&move=up HTTP/1.1\r\n\r\n";
        	
        while(1)
        {        	
          send(sock,send_data2,strlen(send_data2), 0);
          std::cout<<"just sent a message"<<std::endl;
      	 sleep(2);

        }
return 0;
}

```[/PHP]
I don't know what causes the server reset.
thanks in advance.

---

### Post by Zugzwang on 2009-01-29
Probably your server can only handle HTTP/1.0 connections? For these, you have to create a connection and close it for every request. Probably the server also does not like Windows carriage-returns "\r\n".

Also, see here: [http://en.wikipedia.org/wiki/HTTP](http://en.wikipedia.org/wiki/HTTP) - If you use HTTP 1.1, you have to supply the "Host: foo" line.

Anyway, did you try any library for HTTP access? That might be easier and less error-prone.

---

### Post by Adntu on 2009-02-03
> **Zugzwang said:**
> Probably your server can only handle HTTP/1.0 connections? I made sure that it does support HTTP/1.1.
>  Probably the server also does not like Windows carriage-returns "\r\n" I suspect this is the cause.
> Anyway, did you try any library for HTTP access? I tried to find some, but all are for *nix systems, and I have to deploy my application to windows system.
thanks for the help.

---

