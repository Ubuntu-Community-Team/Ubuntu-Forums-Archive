---
title: "how  to name a socket by bind"
date: 2010-10-20
forum: Programming Talk
---

### Post by jamesbon on 2010-10-20
I read the man page of bind but could not understand much.
Here is a small program I posted in one of my previous posts.
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
        unlink("bond_socket");
        server_sockfd = socket(AF_UNIX, SOCK_STREAM, 0);
        server_address.sun_family = AF_UNIX;
        strcpy(server_address.sun_path, "bond_socket");
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
In the above code
the system call bind is used as
```

bind(server_sockfd, (struct sockaddr *)&server_address, server_len);

```
in the arguments of bind I do not see any argument which is the name of socket.
So what is the meaning of naming the socket by bind or I understood some thing wrong?

---

### Post by Some Penguin on 2010-10-20
strcpy(**server_address.sun_path**, "bond_socket");
bind(server_sockfd, (struct sockaddr *)&**server_address**, server_len);

---

### Post by dwhitney67 on 2010-10-20
Ok, we know you can write, but can you read?  You posted two threads the other day -- did you bother to read the replies or even pay attention to Beej's examples, specifically where the socket (file) name was string-copied to the sockaddr_un field of sun_path?

Here's another example, in C:
```

int bindSocketName(int sd, const char* socketName)
{
   struct sockaddr_un sun;

   memset(&sun, 0, sizeof(sun));

   addr.sun_family = AF_UNIX;

   **strncpy(sun.sun_path, socketName, sizeof(sun.sun_path));**

   return bind(sd, (sockaddr*) &sun, SUN_LEN(&sun));
}

```

---

### Post by jamesbon on 2010-10-20
> **dwhitney67 said:**
> Ok, we know you can write, but can you read?   You posted two threads the other day -- did you bother to read the  replies or even pay attention to Beej's examples, specifically where the  socket (file) name was string-copied to the sockaddr_un field of  sun_path?



I read both the threads 
this question is not related to any of those threads hence I opened a new one.
Why is strcpy function used.
Why can't we do 
server_address.sun_path="server_socket"

---

### Post by gmargo on 2010-10-20
Look at the definition of sun_path in **/usr/include/sys/un.h** - sun_path is an array, not a pointer.

---

### Post by jamesbon on 2010-10-21
Ok since the socket is given a name as you people explained above.
Is it possible to see a socket with the given socket name which I assigned as above
 when I am running a server program.
Can netstat or some other command show me the socket with this name.

---

### Post by dwhitney67 on 2010-10-21
I'm not sure if netstat can be used to monitor the existence of a named socket.  However, you could use lsof.

---

