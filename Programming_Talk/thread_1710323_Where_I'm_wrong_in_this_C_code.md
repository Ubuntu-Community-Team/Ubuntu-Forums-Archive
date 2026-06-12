---
title: "Where I'm wrong in this C code"
date: 2011-03-19
forum: Programming Talk
---

### Post by rcbandit on 2011-03-19
Hi,
I'm writing C application which uses Unix Domain Socket for communication. But I can't write the threads in the rigth way. Would you tell me where is my mistake and what is the appropriate way to write it.

How it works:
The idea it to have main thread wich is listening for incomming connections. When the main thread accept connection it passes it to second thread which performs the communication. The server is implemented as Linux daemon.

Server:

```

#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <errno.h>
#include <unistd.h>
#include <syslog.h>
#include <string.h>
#include <sys/socket.h>
#include <sys/un.h>
#include <signal.h>

#include <pthread.h>

#define NTHREADS 5

void *main_thread_function(void *);
void *thread_function(void *client_sockfd);

        int server_sockfd, client_sockfd;
        int server_len, client_len;
        struct sockaddr_un server_address;
        struct sockaddr_un client_address;

void *main_thread_function(void *){

        /*  Accept connection.  */
        client_len = sizeof(client_address);
        client_sockfd = accept(server_sockfd, (struct sockaddr *)&client_address, &client_len);

        int i, j;

        for(i=0; i < NTHREADS; i++)
           {
              pthread_create( &thread_id[i], NULL, thread_function, client_sockfd );
           }

           for(j=0; j < NTHREADS; j++)
           {
              pthread_join( thread_id[j], NULL); 
           }
                

void *thread_function(void *client_sockfd){
                
        /* Accept data */
        char ch;        
        read(client_sockfd, &ch, 1);
        ch++;
        write(client_sockfd, &ch, 1);
        
    }
}

int main(void) {
        
        /* Our process ID and Session ID */
        pid_t pid, sid;
        
        /* Fork off the parent process */
        pid = fork();
        if (pid < 0) {
                exit(EXIT_FAILURE);
        }
        /* If we got a good PID, then
           we can exit the parent process. */
        if (pid > 0) {
                exit(EXIT_SUCCESS);
        }

        /* Change the file mode mask */
        umask(0);
                
        /* Open any logs here */        
                
        /* Create a new SID for the child process */
        sid = setsid();
        if (sid < 0) {
                /* Log the failure */
                exit(EXIT_FAILURE);
        }
                
        /* Change the current working directory */
        if ((chdir("/")) < 0) {
                /* Log the failure */
                exit(EXIT_FAILURE);
        }
        
        /* Close out the standard file descriptors */
        close(STDIN_FILENO);
        close(STDOUT_FILENO);
        close(STDERR_FILENO);
        
        /* Daemon-specific initialization goes here */
        
        /* The Big Loop */
        while (1) {
        

    /*  Remove any old socket and create an unnamed socket for the server.  */

        unlink("/tmp/server_socket");
        server_sockfd = socket(AF_UNIX, SOCK_STREAM, 0);

    /*  Name the socket.  */

        server_address.sun_family = AF_UNIX;
        strcpy(server_address.sun_path, "/tmp/server_socket");
        server_len = sizeof(server_address);
        bind(server_sockfd, (struct sockaddr *)&server_address, server_len);

    /*  Create a connection queue and wait for clients.  */

        listen(server_sockfd, 5);

        signal(SIGCHLD, SIG_IGN);

//        while(1) {

        

    /* Create threads */

           pthread_t main_thread, thread_id[NTHREADS];
           
           pthread_create( &main_thread, NULL, thread_function, NULL );

                          
//        }

        close(client_sockfd);
                    
        }
   exit(EXIT_SUCCESS);
}

```Client:

```

/*  Make the necessary includes and set up the variables.  */

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <sys/un.h>
#include <unistd.h>
#include <stdlib.h>

int main()
{
    int sockfd;
    int len;
    struct sockaddr_un address;
    int result;
    char ch = 'B';

/*  Create a socket for the client.  */

    sockfd = socket(AF_UNIX, SOCK_STREAM, 0);

/*  Name the socket, as agreed with the server.  */

    address.sun_family = AF_UNIX;
    strcpy(address.sun_path, "/tmp/server_socket");
    len = sizeof(address);

/*  Now connect our socket to the server's socket.  */

    result = connect(sockfd, (struct sockaddr *)&address, len);

    if(result == -1) {
        perror("oops: client1");
        exit(1);
    }

/*  We can now read/write via sockfd.  */

    write(sockfd, &ch, 1);
    read(sockfd, &ch, 1);
    printf("char from server = %c\n", ch);
    close(sockfd);
    exit(0);
}

```

---

### Post by AbhiJais on 2011-03-20
hi, I would be glad helping you, but can you please elaborate exactly what are the malfunctioning behaviour does your program show? It would clearly highlight the buggy area of code.

---

### Post by dwhitney67 on 2011-03-20
> **rcbandit said:**
> Hi,
I'm writing C application which uses Unix Domain Socket for communication. But I can't write the threads in the rigth way. Would you tell me where is my mistake and what is the appropriate way to write it.


Forking a separate process and launching a separate thread are not the same.  A separate process will continue running until it exits, regardless of what the parent process does (of course, short of killing the child process!).

For a child thread, the parent thread (generally the main() function) must continue running.  If the parent thread terminates, as does yours in the server code, then the child thread will also terminate.  Obviously, I do not believe this was your intent.

Another issue I see is that you are *not* accepting any connections (contrary to your comments in the OP).  The call to listen() does nothing more than configure the depth of the queue to buffer incoming connections; if your process is busy, and cannot accept() a connection in a timely manner, up to N clients may wait in a pending mode before their connection is accepted.  Any number of clients beyond the N limit will be denied a connection.

Your main_thread_function() seems to have the necessary code to accept a connection, and then service the connected clients.  However this code is never called.

Consider doing something similar to the following outline:
```

1.  Create the Unix Domain socket (that is, set it up, bind, listen).

2.  Accept new connection(s) using accept().  This call will block.

3.  When a connection has been accepted (verify this!), then spawn a thread to handle the connected client.

4.  Loop back to Step 2 to accept() additional connections.

```
If you want your main-thread to do other things, rather than block on the accept() call, then employ the use of select() to monitor your 'server_sockfd' for activity.  If it is time to read, then call accept().

Since it might not be possible to join with your child threads, I would suggest that you set them up to detach from the parent thread so that when they exit, they clean up for themselves.  An alternative is to set up a thread-pool, such that your threads never terminate, but merely handle one client at a time, until the client disconnects.  When a new client connects, reuse one of the existing threads.

Please let me know if you have additional questions.  For now, fix your server code.

P.S.  On further analysis of your code, this while-loop seems problematic as well; without anything to block execution of the code, you are destroying your disk-bound socket and launching a thread each iteration:
```

        /* The Big Loop */
        while (1) {
                ...
        }

```

---

### Post by rcbandit on 2011-03-23
I found a good example how to create Unix domain socket with threads. The problem now is that there is a bug that I can't find

```
#include <stdio.h>
#include <sys/ioctl.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <pthread.h>
#include <sys/un.h>
#include <unistd.h>
#include <stdlib.h>

void* thread_proc(void *arg);

int main(int argc, char *argv[])
{
    struct sockaddr_in server_address;
    int server_sockfd, result;
    int nchildren = 1;
    pthread_t thread_id;
    int x, val;

int server_len, client_len;
    
    if (argc > 1) {
      nchildren = atoi(argv[1]);
    }

    unlink("server_socket");
    server_sockfd = socket(AF_UNIX, SOCK_STREAM, 0);

    val = 1;
    result = setsockopt(server_sockfd, SOL_SOCKET, SO_REUSEADDR, &val, sizeof(val));
    if (result < 0) {
        perror("server5");
        return 0;
    }

    server_address.sin_family = AF_UNIX;
    strcpy(server_address.sun_path, "server_socket");    
    server_address.sin_addr.s_addr = INADDR_ANY;

    result = bind(server_sockfd, (struct sockaddr *) &server_address, sizeof(server_address));
    if (result < 0) {
        perror("exserver5");
        return 0;
    }

    result = listen(server_sockfd, 5);
    if (result < 0) {
        perror("exserver5");
        return 0;
    }

   for (x = 0; x < nchildren; x++) {
    result = pthread_create(&thread_id, NULL, thread_proc, (void *) server_sockfd);
    if (result != 0) {
      printf("Could not create thread.\n");
      return 0;
    }
    sched_yield();
    }

   pthread_join (thread_id, NULL);
}

void* thread_proc(void *arg)
{
  int server_sockfd, sock;
  char buffer[25];
  int nread;

  server_sockfd = (int) arg;

  while (1) {
    sock = accept(server_sockfd, NULL, NULL);
    printf("client connected to child thread %i with pid %i.\n", pthread_self(), getpid());
    nread = recv(sock, buffer, 25, 0);
    buffer[nread] = '\0';
    printf("%s\n", buffer);
    send(sock, buffer, nread, 0);
    close(sock);
    printf("client disconnected from child thread %i with pid %i.\n", pthread_self(), getpid());
  }
}
```There is a problem in this line when I try to compile it.

```
strcpy(server_address.sun_path, "server_socket");
```error: &#8216;struct sockaddr_in&#8217; has no member named &#8216;sun_path&#8217;

can you tell me there is the problem?

---

### Post by dwhitney67 on 2011-03-23
A few of things I noticed (or didn't notice) in your code...

1.  Use struct sockaddr_un, not sockaddr_in.  You need to include <sys/un.h> to get the sockaddr_un declaration.

2.  Clear the sockaddr_un structure, 'server_address', before using it:
```

memset(&server_address, 0, sizeof(server_address));

```

3.  The following is not necessary because it is not applicable to Unix Domain Sockets:
```

server_address.sin_addr.s_addr = INADDR_ANY;

```


P.S.  You should create an array to define your thread IDs.  You use the same variable over and over again, thus preventing you from joining with each child-thread.  All you do now is join with the last created thread.

P.S. #2  Why are you launching N threads for your server socket (i.e. the one that accepts a client connection)??  You should only have one thread (possibly the main-thread) that accepts client connections.  Once a client has connected, then and only then, should you start a thread to handle that one client.  For each client that connects, a separate thread should be launched.  Perhaps you should re-read my previous post.

---

### Post by rcbandit on 2011-03-23
The idea is to create a thread pool to handle the clients.

I have edited the code:

```

/*
    Notes:
    Used technolgies: Unix Domain Socket, Threaded pool
    Configure the number of threads and the path of the socket descriptor
*/

#include <stdio.h>
#include <unistd.h>
#include <pwd.h>
#include <sys/types.h>
#include <syslog.h>
#include <errno.h>
#include <string.h>
#include <sys/stat.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <pthread.h>
#include <sys/un.h>

#define THREADS 1
#define SOCKPATH "/tmp/server_socket"

void* thread_proc(void *arg);

int daemonize(){
    pid_t pid;
    long n_desc;
    int i;

    /* fork the process */
    if ((pid = fork()) != 0) {
          exit(EXIT_FAILURE);
      }

      setsid();

      if ((pid = fork()) != 0) {
          exit(EXIT_FAILURE);
      }

      chdir("/");
      umask(0);

      n_desc = sysconf(_SC_OPEN_MAX);
      for (i = 0; i < n_desc; i++) {
            close(i);
      }

      return 1;
}

int main(int argc, char **argv){

    struct passwd *pws;        
      const char *user = "root"; /* set here the user name in which the daemon will run */

      pws = getpwnam(user);
      if (pws == NULL) {
           printf("Unknown user: %s\n", user);
            return 0;
      }

      daemonize();
  
      /* logging */
      openlog("test_daemon", LOG_PID, LOG_USER);
      syslog(LOG_INFO, "%s", "Hello World!");
      closelog();

      setuid(pws->pw_uid);

      /* do something */

        /* Unix Domain Socket utilization */
        struct sockaddr_un server_address;
            int server_sockfd, result;
        /* Number of the threads */
            pthread_t thread_id;
            int x, val;

        /* Clear the sockaddr_un structure */
        memset(&server_address, 0, sizeof(server_address));

/*             not sure is this needed
            if (argc > 1) {
                  THREADS = atoi(argv[1]);
            }
*/

            unlink(SOCKPATH);
            server_sockfd = socket(AF_UNIX, SOCK_STREAM, 0);

            val = 1;
            result = setsockopt(server_sockfd, SOL_SOCKET, SO_REUSEADDR, &val, sizeof(val));
            if (result < 0) {
            perror("server5");
            return 0;
            }

            server_address.sun_family = AF_UNIX;
            strcpy(server_address.sun_path, SOCKPATH);

            result = bind(server_sockfd, (struct sockaddr *) &server_address, sizeof(server_address));
            if (result < 0) {
            perror("exserver5");
            return 0;
            }

            result = listen(server_sockfd, 5);
            if (result < 0) {
            perror("exserver5");
            return 0;
            }

        /* Create threads for handling connections */
           for (x = 0; x < THREADS; x++) {
            result = pthread_create(&thread_id, NULL, thread_proc, (void *) server_sockfd);
            if (result != 0) {
                  printf("Could not create thread.\n");
                  return 0;
            }
            sched_yield();
            }

        /* Join the created threads */
           pthread_join (thread_id, NULL);

      return 1;
}


void* thread_proc(void *arg){

    int server_sockfd, sock;
      char buffer[25];
      int nread;

      server_sockfd = (int) arg;

      while (1) {
            sock = accept(server_sockfd, NULL, NULL);
   
            nread = recv(sock, buffer, 25, 0);
            printf("%s\n", buffer);
            send(sock, buffer, nread, 0);
            close(sock);

    
    sleep(1);    /* not sure is it needed */
    }
}

```

---

### Post by dwhitney67 on 2011-03-23
> **rcbandit said:**
> The idea is to create a thread pool to handle the clients.

I have edited the code:


Yes; the code is indeed different.  Why are you attempting to run the app as a daemon at this time?  You haven't even gotten the fundamentals of the app working yet.

As I indicated earlier, and will for the last time, your server needs to accept a connection, _and then_ handle receive/send from the client.  This ain't rocket science, so hopefully this time this notion will sink in.

For now, I suggest that your forget about the daemon-ization of your application, forget about the thread-pool, and threading altogether, and get your application working with a single client.  Also try to modularize the application, such that each individual task is reduced to a function call.  It will make your application easier to read.

When you have completed this trivial suggestions above, consider creating a thread-pool model.  This should be implemented in a separate module (that is, define the interface in a .h file, and implement it in a .c file).

A thread-pool requires N threads; these threads should remain *idle* until given a client socket descriptor, at which point it then should handle the client connection.  When the client disconnects, then the thread should return to the *idle* state.  Consider the use of a state flag to indicate if a thread is available or not.

---

### Post by rcbandit on 2011-03-23
The idea here is that this daemon is the core of the application. Another 4 modules will run as clients. This Core implemented as daemon will only exchange JSON strings between the client modules. 

> 
As I indicated earlier, and will for the last time, your server needs to accept a connection, _and then_ handle receive/send from the client.  This ain't rocket science, so hopefully this time this notion will sink in.
Now I'm working on that.

---

