---
title: "Server.c clients can connect but can not reconnect"
date: 2014-08-01
forum: Programming Talk
---

### Post by brick2 on 2014-08-01
```
#include <sys/socket.h>
#include <sys/types.h>
#include <arpa/inet.h>
#include <pthread.h>
#include <stdio.h>
#include <unistd.h>


struct arguments
        {
            int *new_sock;
            int port;
            char *IP;
        };

#define cli_num 100
static int index01 = 0;
pthread_t cli[cli_num];
int cli_sock[cli_num];
int sock_fd;

int connection();
int *cli_handler(void *arg);
int cli_CMD();

int main( int argv, char* const argc[] )
{
    pthread_t cli_command;
    pthread_create( &cli_command, NULL, cli_CMD, NULL );
    pthread_detach(&cli_command);
    connection();
    return 0;
}

int connection()
{
    int len,
        PORT = 4444;
    struct sockaddr_in server;

    server.sin_family = AF_INET;
    server.sin_port = htons(PORT);
    server.sin_addr.s_addr = INADDR_ANY;

    /* bind
     * listen
     * accept
     */

    sock_fd = socket( AF_INET, SOCK_STREAM, 0);

    if( sock_fd == -1 )
    {
        perror("SOCKET FAILED!!!");
        return 1;
    }
    puts("SOCKET CREATED");

    if( bind( sock_fd, (struct sockaddr*)&server, sizeof(server) ) == -1 )
    {
        perror("BIND FAILED!!!");
        return 1;
    }
    puts("BIND DONE");

    listen(sock_fd, 100);
    //why does printf not output text here? but no errors are given
    puts("LISTENING ON PORT 4444....");

    len = sizeof(struct sockaddr_in);
    int index00;

    struct arguments *ptr_arg;

point00:while( cli_sock[index01] = accept (sock_fd, (struct sockaddr  *) &server, (socklen_t *)&len) )
        {
            if(cli_sock == -1)
            {
                perror("ACCEPT FAILED!!!");
                return 1;
            }
            ptr_arg = (struct arguments *)malloc(sizeof(*ptr_arg));
            ptr_arg->new_sock = cli_sock[index01];


            ptr_arg->IP = inet_ntoa(server.sin_addr);
            ptr_arg->port = ntohs(server.sin_port);

            //why would someone put < 0 here

            for( index00=0; index00<cli_num; index00++ )
            {
                if( cli[index00] == NULL )
                {
                    if( pthread_create( &cli[index00], NULL, cli_handler, (void *)ptr_arg ) < 0 )
                    {
                        perror("THREAD FAILED");
                        return 1;
                    }
                    //pthread_join(cli[index00], NULL);
                    pthread_detach(cli[index00]);
                    printf( "Connection received from: %s %d \n", inet_ntoa(server.sin_addr), ntohs(server.sin_port) );
                    index01++;
                    goto point00;
                }
                index00++;
            }
        }
}

int *cli_handler(void *arg)
{
    int new_sock,// = *(int *)sock,
        write_fd,
        recv_fd,
            i,
            indexTMP00 = index01;

    char buff[256];

    struct arguments *ptr_arg;
    ptr_arg = (struct arguments *)arg;

    new_sock = ptr_arg->new_sock;
    int port_f = ptr_arg->port;

    int len = strlen(ptr_arg->IP);
    char cli_id[len];
    for( i=0; i<len; i++ )
        cli_id[i] = ptr_arg->IP[i];
    for( i=0; i<len; i++ )
        ptr_arg->IP[i] = '\0';

    //printf("FROM %s %d: %s", cli_id, port_f, buff);
    //printf("FROM %s %d: %s, index = %d: %s \n", port_f, cli_id, indexTMP00, buff);
    while(1)
    {
        write_fd = write( new_sock, "TEST: ", 6 );
        if( write_fd == 0 )
        {
            close(new_sock);
            cli_sock[indexTMP00] = NULL;
            index01--;
            printf("NOTHING WRITTEN, client %s %d disconnected: \n", cli_id, port_f);
            return 1;
        }
        else if( write_fd == -1 )
        {
            close(new_sock);
            cli_sock[indexTMP00] = NULL;
            index01--;
            printf("Client %s %d disconnected: \n", cli_id, port_f);
            perror("FAILED TO WRITE");
            return 1;
        }

        if ( ( recv_fd = recv( new_sock, buff, 256, 0 ) ) == -1 )
        {
            close(new_sock);
            cli_sock[indexTMP00] = NULL;
            index01--;
            printf("Client %s %d disconnected: \n", cli_id, port_f);
            perror("FAILED TO RECV: ");
            return 1;
        }
        printf("FROM %s %d: %s", cli_id, port_f, buff);
        for( i=0; i<256; i++ )
            buff[i] = '\0';
    }
    close(new_sock);
    cli_sock[indexTMP00] = NULL;
    index01--;
    free(arg);
}

int cli_CMD()
{
    //printf("Enter cli num first than space and command you wish to issue\n");
    char CMD[256];
    int i, indexTMP00, write_fd, indexTMP01 = index01;
point01:while(1)
        {
            scanf("%d", &indexTMP00);
            fgets(CMD, 256, stdin);

            write_fd = write( cli_sock[indexTMP00], CMD, strlen(CMD) );
            if(write_fd = 0)
            {
                cli_sock[indexTMP01] = NULL;
                perror("NO CMD SENT: ");
                goto point01;
            }
            else if(write_fd == -1)
            {
                cli_sock[indexTMP01] = NULL;
                perror("FAILED TO WRITE CMD: ");
                goto point01;
            }

            printf("TO %d %s: \n", indexTMP00, CMD);
            for( i=0; i<256; i++ )
                CMD[i] = '\0';
        }
}
```


I can connect clients without problems. For now I just use netcat for testing purposes as I did not make the client yet. I can choose to which client to send a message and it is sent to only that client, clients can also send messages to the server and that part goes well.
Now the problem comes in to being when I disconnect a client and try to reconnect it. the connection succeeds but it just hangs here are some samples bellow.



SOCKET CREATED
BIND DONE
LISTENING ON PORT 4444....
Connection received from: 192.168.1.2 61000 
Connection received from: 192.168.1.2 32768

FROM 192.168.1.2 61000: bla
FROM 192.168.1.2 32768: fsafe

TO 0  afaswdf
TO 1  fqq


FROM 192.168.1.2 32768: FROM 192.168.1.2 32768: Client 192.168.1.2 32768 disconnected: FAILED TO WRITE: Broken pipe    
//When I disconnect a client this happens, I do not  know  why FROM message is printed twice. the rest of this line is as it should be

//Than when I try to reconnect a client I get
Connection received from: 192.168.1.2 32769 FAILED TO WRITE: Bad file descriptor


Now I am guessing that I am making a mistake somewhere with the indexing of socket descriptors but can not seam to find the error.
Could anyone shed some light on the matter.

---

### Post by dwhitney67 on 2014-08-03
What is the point of this statement (i.e. the for-loop in general)?
```

            for( index00=0; index00<cli_num; index00++ )

```
And this?
```

    int len = strlen(ptr_arg->IP);
    char cli_id[len];
    for( i=0; i<len; i++ )
        cli_id[i] = ptr_arg->IP[i];
    for( i=0; i<len; i++ )
        ptr_arg->IP[i] = '\0';

```
write()?  Although basically equivalent, just use send().
```

write_fd = write( new_sock, "TEST: ", 6 );

```
When a client disconnects, it sends 0 bytes, not -1 bytes.  You need something better to get out of the while-loop.
```

if ( ( recv_fd = recv( new_sock, buff, 256, 0 ) ) == -1 )

```


P.S.  Read the man-pages:
man send
man recv
man accept

---

### Post by brick2 on 2014-08-04
```
for( index00=0; index00<cli_num; index00++ )
```
refers to the pthread cli[cli_num]
checks for NULL if NULL then it is free if not there is another thread or so I think it functions.
Limits the number of threads possible.


```
int len = strlen(ptr_arg->IP);
    char cli_id[len];
    for( i=0; i<len; i++ )
        cli_id[i] = ptr_arg->IP[i];
    for( i=0; i<len; i++ )
        ptr_arg->IP[i] = '\0'
```;


Now this take the ip address string and puts it in another string, and it cleans up the global string for IP from which it has take the IP, so that the addresses would not be duplicated.

---

### Post by brick2 on 2014-08-04
```
if ( ( recv_fd = recv( new_sock, buff, 256, 0 ) ) == -1 )
```


recv_fd is jsut a descriptor and it says in the man pages that is the function returns -1 if it failes to recieve on a nonblocking socket.

---

### Post by dwhitney67 on 2014-08-04
What I was attempting to allude to earlier is that the for-loop is not required.  In fact, you probably do not even need to declare a global array of pthread_t ids.

Consider the following (pseudo/untested code):
```

while (true)
{
    int client_sock = accept(listen_sock, (struct sockaddr*) &server, (socklen_t*) &len);

    if (client_sock <= 0)
    {
        continue;
    } 

    struct arguments* args = malloc(sizeof(*ptr_arg));
    args->new_sock = client_sock;
    args->IP = inet_ntoa(server.sin_addr);
    args->port = ntohs(server.sin_port);

    pthread_t tid;
    pthread_attr_t* attr = malloc(sizeof(struct pthread_attr_t));

    pthread_attr_init(attr);
    pthread_attr_setdetachedstate(attr, PTHREAD_CREATE_DETACHED);

    pthread_create(&tid, attr, cli_handler, (void*) args);
}

```

---

### Post by dwhitney67 on 2014-08-04
For the client handler, something like this might just work:
```

void cli_handler(void* arg)
{
    struct arguments* args = (struct arguments*) arg;

    const char* greeting = "TEST:";

    send(args->new_sock, greeting, strlen(greeting), 0);

    char buf[1024];
    int bytesRead = 0;

    while ((bytesRead = recv(args->new_sock, buf, sizeof(buf) - 1, 0) > 0)
    {
        buf[bytesRead] = '\0';

        printf("Client sent this message: %s\n", buf);
    }

    close(args->new_sock);

    free(args);

    pthread_exit(NULL);
}

```

P.S.  You are not specifically setting up your sockets to be non-blocking, thus calls to accept() and read() will block.

---

### Post by ofnuts on 2014-08-04
> **dwhitney67 said:**
> What I was attempting to allude to earlier is that the for-loop is not required.  In fact, you probably do not even need to declare a global array of pthread_t ids.


Already mentioned in  [http://ubuntuforums.org/showthread.php?t=2236553](http://ubuntuforums.org/showthread.php?t=2236553)  : )

To the OP: best keep everything in a single thread. Making one topic for each problem you have doesn't make very easy for us to understand where you stand. Your problems stem more from your basic design/understanding than from anecdotal difficulties with specific APIs.

---

