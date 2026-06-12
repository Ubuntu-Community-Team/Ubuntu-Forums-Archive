---
title: "[SOLVED] execute command with execlp() and pipe to tcp socket"
date: 2009-01-01
forum: Programming Talk
---

### Post by huseyinkozan on 2009-01-01
I couldnt find with searching, if this was spoken before sorry.

I want to make a server program which will run commands on remote console, (for now with telnet)
I wrote some code like below, but when I take the command with recv() and pass the char array to execlp() (or execve,execl...) stderr says:

:not found

But when I pass an direct string like "ls" it works.

Where I am wrong ?

Thanks

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <sys/wait.h>
#include <signal.h>

#define MYPORT 3456
#define BACKLOG 10

void sigchild_handler(int s)
{
    while(wait(NULL)>0);
}

int main(int argc, char * argv[])
{
    int sockfd, newfd;
    struct sockaddr_in my_addr;
    struct sockaddr_in their_addr;
    int sin_size;
    struct sigaction sa;
    int yes = 1;

    if( (sockfd = socket(AF_INET, SOCK_STREAM, 0) ) == -1 )
    {
        perror("socket");
        return EXIT_FAILURE;
    }

    if( (setsockopt(sockfd, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int))) == -1 )
    {
        perror("setsockopt");
        return EXIT_FAILURE;
    }

    my_addr.sin_family = AF_INET;
    my_addr.sin_port = htons(MYPORT);
    my_addr.sin_addr.s_addr = INADDR_ANY;
    memset(&(my_addr.sin_zero),'\0',8);

    if( bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr)) == -1 )
    {
        perror("bind");
        return EXIT_FAILURE;
    }

    if( listen(sockfd, BACKLOG) == -1 )
    {
        perror("listen");
        return EXIT_FAILURE;
    }

    sa.sa_handler = sigchild_handler;
    sigemptyset(&sa.sa_mask);
    sa.sa_flags = SA_RESTART;

    if( sigaction(SIGCHLD, &sa, NULL) == -1 )
    {
        perror("sigaction");
        return EXIT_FAILURE;
    }

    while(1)
    {
        int st;
        sin_size = sizeof(struct sockaddr_in);
        if( (newfd = accept(sockfd, (struct sockaddr*) &their_addr, (socklen_t*)&sin_size)) == -1 )
        {
            perror("accept");
            continue;
        }

        printf("Server got connection from %s\n", inet_ntoa(their_addr.sin_addr));

        pid_t pid = fork();
        if( pid == 0 )
        {
            close(sockfd);


            char commbuff[80] = {0};
            char commbuffer[80] = {0};

            size_t r;
            if( (r = recv(newfd, commbuff, 79, 0)) == -1)
            {
                perror("recv");
            }

            commbuff[r]='\n';

            //sprintf(commbuffer, "/bin/sh -c \"%s\"",commbuff);

            dup2(newfd, 2);
            dup2(newfd, 1);
            dup2(newfd, 0);
            close(newfd);

            //system( commbuffer );
            execlp("/bin/sh", "sh", "-c", commbuff,(char *)NULL);

            perror("Couldn't exec");
            return EXIT_FAILURE;
        }
        else
        {
            close(newfd);
            waitpid(pid, &st, 0);
        }
    }

    return EXIT_SUCCESS;
}

```

---

### Post by doorman on 2009-01-01
Upon the receipt of the message, you should end the string, not append an '\n', since there's very little chance you have a 0 immediately following it.

So, instead of
[PHP]commbuff[r] = '\n';
[/PHP]
there should be
[PHP]commbuff[r] = 0;
[/PHP]

---

### Post by huseyinkozan on 2009-01-02
thanks doorman, but it is same

---

### Post by doorman on 2009-01-02
hm...

did you try to printf what you get from the client? is the string correct? Also, when you say you "pass a direct string like 'ls'" - what do you mean exactly by that?

---

### Post by public_void on 2009-01-02
Check the return value of the recv() call more thoroughly because recv() will return when data has been received of any length up to the buffer length. It's probably unlikely for a recv() to encounter a partial send because you are sending small amounts of data, but if the data is split into more than one chunk you need to recv() all the data. Also the client may send more data than the buffer size resulting in commands being truncated. These problems now raise the issue of a simple protocol for the client to indicate when all the data has been sent and when the server closes the connection. The simplest protocol is the client ends command data with \r\n. The server receives data until it reads \r\n, at which point it closes the connection to the client. It can become more complicated, i.e. the connection remaining open for more commands to be received or the client prefixes a simple header to a command with the size of the data being sent. It is probably best to keep it simple for now, however introducing data headers are definitely worth doing for more robust communication.

The simplest way to write this is: malloc a receive buffer in which received data is appended to, if more space is needed realloc the buffer. The call to recv() should be in a loop checking the return value of recv() to get the amount of bytes received, if the client has closed the connection or if an error occurred. Each chunk of data will need to be checked for the terminator \r\n. If not present append to the buffer, when encountered discard all data after the terminator, append to the buffer and close the connection the client. If the client closes the connection before the terminator is found the buffer should be discarded because the data is likely to be a partial send. The receive buffer will need pointers to track the start and append locations of the buffer, adjusted when necessary.

For more help check the man pages or [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/"), a brilliant guide for an introduction to Linux network programming.

---

### Post by huseyinkozan on 2009-01-02
> **doorman said:**
> hm...

did you try to printf what you get from the client? is the string correct? Also, when you say you "pass a direct string like 'ls'" - what do you mean exactly by that?

yes, I print the string (and tried add '\n' or '\0' at end of it) and it is correct.

this doesnt work:
execlp("/bin/sh", "sh", "-c", (const char *) commbuff,(char *)NULL);

this works and gives me the directory list to the far side, connected client:
execlp("/bin/sh", "sh", "-c", "ls",(char *)NULL);

can dup2()s be the problem ?
I mean, maybe execlp() runs before the recv()
how can I test this ?

---

### Post by huseyinkozan on 2009-01-02
Thank you very much boys, doorman for interest and public_void for the trick.
I read the Beej's guide in a translated and old format, but I missed the recv concept. Rremarking the comming data with recv() solved for now. I got the data in a loop.

---

