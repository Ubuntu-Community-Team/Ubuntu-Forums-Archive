---
title: "simple &quot;telnet&quot; program ?"
date: 2007-10-08
forum: Programming Talk
---

### Post by Ne0z on 2007-10-08
Hi 
i need to write a simple program that transfers text files over the ethernet port from one pc to another. Im not sure how to do it, would be glad if someone gave me some heading on it :). 

Do i use sockets to open the connection ?

What else should i take note of ?


Thank you for your help !

Cheers

---

### Post by ghostdog74 on 2007-10-08
do you need to reinvent the wheel? if not, there are tools like FTP,SCP,SFTP etc you can use.

---

### Post by gnusci on 2007-10-08
Socket is good:

[http://linuxgazette.net/issue74/tougher.html](http://linuxgazette.net/issue74/tougher.html)

But if you wanna go farther, just give a look to MICO:

[http://www.mico.org/](http://www.mico.org/)

---

### Post by pmasiar on 2007-10-08
Is this a learning exercise? Are you restricted in language selection?

Python has modules to handle this type of tasks quite simple. Another option might be bash, but Python is more universal (better return od your time invested) IMHO.

---

### Post by slavik on 2007-10-08
Perl is probably simpler in this regard, you can get simple client/server thing going in about 10-15 lines.

ftp should be easier to use though

---

### Post by ryno519 on 2007-10-08
> **Ne0z said:**
> Hi 
i need to write a simple program that transfers text files over the ethernet port from one pc to another. Im not sure how to do it, would be glad if someone gave me some heading on it :). 

Do i use sockets to open the connection ?

What else should i take note of ?


Thank you for your help !

Cheers

This sounds like homework. :)

What did your professor say? Did he give you any restrictions? Such as you have to do it in C/C++ and it has to be done with sockets. If that's the case it will be a little more difficult than simply using an existing protocol. That being said, sending a simple text file over the network using tcp/ip sockets isn't incredibly difficult.

---

### Post by Ne0z on 2007-10-08
hi guys,

i just need to send strings across the network. 

i was using this program from a linux textbook 

the server

> 
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>

int main(argc, argv)
{
        int s, fd, len;
        struct sockaddr_in my_addr;
        struct sockaddr_in remote_addr;
        int sin_size;
        char buf[BUFSIZ];

        memset(&my_addr, 0, sizeof(my_addr));
        my_addr.sin_family = AF_INET;
        my_addr.sin_addr.s_addr = inet_addr("10.1.1.1");
        my_addr.sin_port = htons(8000);

        if ((s = socket(AF_INET, SOCK_STREAM, 0)) < 0)
        {
                perror("socket");
                return 1;
        }

        if (bind(s, (struct sockaddr *)&my_addr, sizeof(struct sockaddr)) < 0)
        {
                perror("bind");
                return 1;
        }

        listen(s, 5);
        sin_size = sizeof(struct sockaddr_in);
        if ((fd = accept(s, (struct sockaddr *)&remote_addr, &sin_size)) < 0)
        {
                perror("accept");
                return 1;
        }
        printf("accepted client %s\n", inet_ntoa(remote_addr.sin_addr));
        len = send(fd, "Welcome to my server\n", 21, 0);
        while ((len = recv(fd, buf, BUFSIZ, 0)) > 0)
        {
                buf[len] = '\0';
                printf("%s\n", buf);
                if (send(fd, buf, len, 0) < 0)
                {
                        perror("write");
                        return 1;
                }
        }
        close(fd);
        close(s);
	       return 0;
}


and the Client

> 
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>

int main(argc, argv)
{
        int s, len;
        struct sockaddr_in remote_addr;
        char buf[BUFSIZ];

        memset(&remote_addr, 0, sizeof(remote_addr));
        remote_addr.sin_family = AF_INET;
        remote_addr.sin_addr.s_addr = inet_addr("10.1.1.2");
        remote_addr.sin_port = htons(8000);

        if ((s = socket(AF_INET, SOCK_STREAM, 0)) < 0)
        {
                perror("socket");
                return 1;
        }

        if (connect(s, (struct sockaddr *)&remote_addr, sizeof(struct sockaddr)) < 0)
        {
                perror("connect");
                return 1;
        }

        printf("connected to server\n");
        len = recv(s, buf, BUFSIZ, 0);
        buf[len] = '\0';
        printf("%s", buf);
        while(1)
        {
                printf("Enter string to send: ");
                scanf("%s", buf);
                if (!strcmp(buf, "quit"))
                        break;
                len = send(s, buf, strlen(buf), 0);
                len = recv(s, buf, BUFSIZ, 0);
                buf[len] = '\0';
                printf("  received: %s\n", buf);
        }

        close(s);
        return 0;
}



i started the server on a pc and the client on another through a cross cable . i've got this problem 

Connection Refused. 

i've tried turning off the firewall. but i still get this problem. 

what can i do ?

---

### Post by ryno519 on 2007-10-08
C sockets are a little rusty. Lets see...

It appears to be a problem with the IP address you set your server as. At least, that's my best initial guess. Try changing it to accept connections from any incoming address and double check and make sure the ip address you're trying to connect to in your client is actually the servers IP.

---

### Post by Ne0z on 2007-10-08
is it possible that i have to set something in inetd.conf for the computer at the server side ?

---

### Post by ryno519 on 2007-10-08
> **Ne0z said:**
> is it possible that i have to set something in inetd.conf for the computer at the server side ?

You shouldn't have to.

---

### Post by Jacks0n on 2007-10-09
netcat?

server:
```
cat file | nc -l -p 5600
```

client:
```
nc 127.0.0.1 5600 > file2
```

---

