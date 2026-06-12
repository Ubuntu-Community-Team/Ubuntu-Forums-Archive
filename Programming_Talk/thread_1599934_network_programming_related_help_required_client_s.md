---
title: "network programming related help required client server program"
date: 2010-10-18
forum: Programming Talk
---

### Post by jamesbon on 2010-10-18
Hi,
I am reading and understanding code from a book.
I am copy pasting the exact code which I have.
Following program is for client.c
```

#include<sys/types.h>
#include<sys/socket.h>
#include <stdio.h>
#include <sys/un.h>
#include <unistd.h>>
#include <stdlib.h>
int main() {
int sockfd;
int len;
struct sockaddr_un address;
int result;
char ch = 'A';
        sockfd = socket(AF_UNIX, SOCK_STREAM, 0);
        address.sun_family = AF_UNIX;
        strcpy(address.sun_path, "server_socket");

```
I was not able to understand the use of server_socket in above strcpy function.
Where does this come to picture

```

        len = sizeof(address);
        result = connect(sockfd, (struct sockaddr *)&address, len);
        if(result == -1) {
        perror("oops: client1");
        exit(1);
        }

write(sockfd, &ch, 1);
read(sockfd, &ch, 1);
printf("char from server = %c\n", ch);
close(sockfd);
exit(0);
}


```
When I run the code as 
```
gcc client.c -o client.o
```
then on terminal I see each time letter B why is that happening.


and following program is for server.c
```

#include<sys/types.h>
#include<sys/socket.h>
#include<stdio.h>
#include <sys/un.h>
#include <unistd.h>
#include<stdlib.h>
int main()
{
        int server_sockfd, client_sockfd;
        int server_len, client_len;
        struct sockaddr_un server_address;
        struct sockaddr_un client_address;
        unlink("server_socket");
        server_sockfd = socket(AF_UNIX, SOCK_STREAM, 0);
        server_address.sun_family = AF_UNIX;
        strcpy(server_address.sun_path, "server_socket");

```
I am not clear with use of server_address.sun_path 
I understand that server_address is a struct of type sockaddr_un
but what is sun_path I had seen the file linux/un.h
but could not understand.

```

        server_len = sizeof(server_address);
        bind(server_sockfd, (struct sockaddr *)&server_address, server_len);
        listen(server_sockfd, 5);
        while (1) {
                char ch;
                printf("server waiting\n");
                client_len = sizeof(client_address);
                client_sockfd = accept(server_sockfd,
                                       (struct sockaddr *)&client_address,
                                       &client_len);
                read(client_sockfd, &ch, 1);
                ch++;
                write(client_sockfd, &ch, 1);
                close(client_sockfd);
        }
}


```

---

### Post by dwhitney67 on 2010-10-18
In short, it is a socket file.  While the server is running, examine the current working directory from which the server was launched... you should see a file with the name "server_socket=".

---

### Post by gmargo on 2010-10-18
> **jamesbon said:**
> When I run the code .... then on terminal I see each time letter B why is that happening.

 
The client connects to the server and send a single character 'A'.  The server receives a connection from the client and reads a single character, increments it ('A' + 1 = 'B'), and sends it back to the client. So the client prints 'char from server = B', indicating that your round trip data transfer was successful.

> 
I am not clear with use of server_address.sun_path 
For a unix-family socket (AF_UNIX), the "sun_path" field refers to a path in the filesystem, where a socket device will be created.  When the server is running, you should have a socket device file in the current directory named "server_socket" with permissions like "srwxr-xr-x".  Note the leading "s" which means socket.
```

$ ls -lgG | grep socket
srwxr-xr-x 1    0 Oct 18 11:27 server_socket

```

---

### Post by jamesbon on 2010-10-20
Why is the name sun_path used I mean why is sun word used is it proprietary?

---

### Post by dwhitney67 on 2010-10-20
**s**ockaddr_**un** ---> sun

Conversely, oftentimes in socket related code you will see "sin", which is derived from sockaddr_in... not from Adam & Eve.

---

### Post by jamesbon on 2010-10-21
Ok.

---

