---
title: "Please help me understand this Multiperson chat server cod"
date: 2012-03-04
forum: Programming Talk
---

### Post by geewhan on 2012-03-04
Hey guys, I would like to know if someone could tell me step by step what these commands does.

I know this code is a multiperson chat server which I got it off from a site, but not a full description. I also know there are comments but I am still having trouble understanding them.

The reason why I ask is because I want to write a code something like this, but I do not know where to start writing one. I understand the basic of socket coding but not advance like this.

Thank for your time

```


/*
** selectserver.c -- a cheezy multiperson chat server
*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

#include <arpa/inet.h>
#include <netdb.h>
#define PORT "9034"   // port we're listening on
// get sockaddr, IPv4 or IPv6:
void *get_in_addr(struct sockaddr *sa)
{
    if (sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }
    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}
int main(void)
{
    fd_set master;    // master file descriptor list
    fd_set read_fds;  // temp file descriptor list for select()
    int fdmax;        // maximum file descriptor number
    int listener;     // listening socket descriptor
    int newfd;        // newly accept()ed socket descriptor
    struct sockaddr_storage remoteaddr; // client address
    socklen_t addrlen;
    char buf[256];    // buffer for client data
    int nbytes;
    char remoteIP[INET6_ADDRSTRLEN];
    int yes=1;        // for setsockopt() SO_REUSEADDR, below
    int i, j, rv;
    struct addrinfo hints, *ai, *p;
    FD_ZERO(&master);    // clear the master and temp sets
    FD_ZERO(&read_fds);
    // get us a socket and bind it
    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_flags = AI_PASSIVE;
    if ((rv = getaddrinfo(NULL, PORT, &hints, &ai)) != 0) {
        fprintf(stderr, "selectserver: %s\n", gai_strerror(rv));
        exit(1);
    }
    
    for(p = ai; p != NULL; p = p->ai_next) {
        listener = socket(p->ai_family, p->ai_socktype, p->ai_protocol);
        if (listener < 0) { 
            continue;
        }
        
        // lose the pesky "address already in use" error message
        setsockopt(listener, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int));
        if (bind(listener, p->ai_addr, p->ai_addrlen) < 0) {
            close(listener);
            continue;
		}
             break;
    }
    // if we got here, it means we didn't get bound
    if (p == NULL) {
        fprintf(stderr, "selectserver: failed to bind\n");
        exit(2);
    }
    freeaddrinfo(ai); // all done with this
    // listen
    if (listen(listener, 10) == -1) {
        perror("listen");
        exit(3);
    }
    // add the listener to the master set
    FD_SET(listener, &master);
    // keep track of the biggest file descriptor
    fdmax = listener; // so far, it's this one
    // main loop
    for(;;) {
        read_fds = master; // copy it
        if (select(fdmax+1, &read_fds, NULL, NULL, NULL) == -1) {
            perror("select");
            exit(4);
        }
        // run through the existing connections looking for data to read
        for(i = 0; i <= fdmax; i++) {
            if (FD_ISSET(i, &read_fds)) { // we got one!!
                if (i == listener) {
                    // handle new connections
                    addrlen = sizeof remoteaddr;
                    newfd = accept(listener,
                        (struct sockaddr *)&remoteaddr,
                        &addrlen);
                    if (newfd == -1) {
                        perror("accept");
                    } else {
                        FD_SET(newfd, &master); // add to master set
                        if (newfd > fdmax) {    // keep track of the max
                            fdmax = newfd;
                        }
                        printf("selectserver: new connection from %s on "
                            "socket %d\n",
                            inet_ntop(remoteaddr.ss_family,
                                get_in_addr((struct sockaddr*)&remoteaddr),
                                remoteIP, INET6_ADDRSTRLEN),
                            newfd);
                    }
                } else {
                    // handle data from a client
                    if ((nbytes = recv(i, buf, sizeof buf, 0)) <= 0) {
                        // got error or connection closed by client
                        if (nbytes == 0) {
                            // connection closed
   			printf("selectserver: socket %d hung up\n", i);
                        } else {
                            perror("recv");
                        }
                        close(i); // bye!
                        FD_CLR(i, &master); // remove from master set
                    } else {
                        // we got some data from a client
                        for(j = 0; j <= fdmax; j++) {
                            // send to everyone!
                            if (FD_ISSET(j, &master)) {
                                // except the listener and ourselves
                                if (j != listener && j != i) {
                                    if (send(j, buf, nbytes, 0) == -1) {
                                        perror("send");
                                    }
                                }
                            }
                        }
                    }
                } // END handle data from client
            } // END got new incoming connection
        } // END looping through file descriptors
    } // END for(;;)--and you thought it would never end!
    
    return 0;
}



```

---

### Post by muteXe on 2012-03-05
google

[http://www.tenouk.com/cnlinuxsockettutorials.html](http://www.tenouk.com/cnlinuxsockettutorials.html)

---

### Post by ofnuts on 2012-03-05
> **muteXe said:**
> google

[http://www.tenouk.com/cnlinuxsockettutorials.html](http://www.tenouk.com/cnlinuxsockettutorials.html)
See also "man 2 select" (waiting simultaneously on several streams).

---

### Post by geewhan on 2012-03-05
Could someone please tell me what is the difference between child and parent when using the fork() command.

Also how the fork() command is used.

Is there another site you could refer. The one you posted is a bit difficult to understand.

Thanks

---

### Post by r-senior on 2012-03-06
[https://en.wikipedia.org/wiki/Fork_%28operating_system%29](https://en.wikipedia.org/wiki/Fork_%28operating_system%29)

[http://www.linuxquestions.org/questions/programming-9/c-programming-fork-248958/](http://www.linuxquestions.org/questions/programming-9/c-programming-fork-248958/)

---

### Post by ofnuts on 2012-03-06
> **geewhan said:**
> Could someone please tell me what is the difference between child and parent when using the fork() command.

Also how the fork() command is used.

Is there another site you could refer. The one you posted is a bit difficult to understand.

Thanks
After the call to "fork" your program has split itself in two identical process ( bit like a bacteria): same memory content (variable values are the same, file handles are the same). The only difference between parent and child is the "fork" return value: 0 for a child, and pid of child in the parent. So typically this is used this way: 

```

int main {
  int count=0
  for (;;) {
     wait_for_some_reason_to_start_a_child();
     count++;
     pid=fork();
     if (!pid) {
        thingsDoneAsChild();
        break;
     }
     else {
        // we are the parent, manage the child
        store_child_pid(pid);
    }
}

```

In the pseudo code above the child process will see the same value for "count" as the parent (up to the fork). In other words, it can use "count" as its "child number" (but this value has been duplicated at fork time, if it modifies it, this won't change its value for the parent process).

---

