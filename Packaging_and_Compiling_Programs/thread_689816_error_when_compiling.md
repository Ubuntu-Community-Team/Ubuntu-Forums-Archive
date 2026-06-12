---
title: "error when compiling"
date: 2008-02-06
forum: Packaging and Compiling Programs
---

### Post by arvindenrique on 2008-02-06
this is the error when trying to compile this program.i have installed all necessary lib files and gcc.
> arvind@arvind:~$ gcc -o hello hello.c
hello.c: In function ‘main’:
hello.c:4: error: stray ‘\342’ in program
hello.c:4: error: stray ‘\200’ in program
hello.c:4: error: stray ‘\234’ in program
hello.c:4: error: ‘Hello’ undeclared (first use in this function)
hello.c:4: error: (Each undeclared identifier is reported only once
hello.c:4: error: for each function it appears in.)
hello.c:4: error: expected ‘)’ before ‘World’
hello.c:4: error: stray ‘\342’ in program
hello.c:4: error: stray ‘\200’ in program
hello.c:4: error: stray ‘\235’ in program
hello.c:5: warning: incompatible implicit declaration of built-in function ‘exit’


This is a simple hello world program

---

### Post by peabody on 2008-02-06
> **arvindenrique said:**
> this is the error when trying to compile this program.i have installed all necessary lib files and gcc.


This is a simple hello world program

It's going to be awful hard to tell you what's wrong if you don't post your code.

---

### Post by arvindenrique on 2008-02-07
This is the code

> #include <stdio.h>
int main()
{
    printf(“Hello World\n”);
    exit(0);
}

---

### Post by Rui Pais on 2008-02-07
Theres nothing wrong with your code (although you should use **return (0);** instead of **exit(0);** ...)

The problem it's that you probabilly don't have a full compiler set installed.

Try:
```
sudo apt-get install build-essential
```
first.

---

### Post by hod139 on 2008-02-08
Also, make sure the string "Hello World\n" is inside double quotes, not two single quotes.

---

### Post by stroyan on 2008-02-08
The problem is not a lack of build-essential packages.
(Not yet, anyway.)

The problem is that you are using wierd unicode quote characters instead of proper ascii double quotes.
You have “Hello World\n”.
You need "Hello World\n".

I wonder if you used a text editor that tried to be helpful and replaced normal double quotes with those fancy and inappropriate ones.

---

### Post by Rui Pais on 2008-02-08
> **stroyan said:**
> The problem is not a lack of build-essential packages.
(Not yet, anyway.)

The problem is that you are using wierd unicode quote characters instead of proper ascii double quotes.
You have “Hello World\n”.
You need "Hello World\n".

I wonder if you used a text editor that tried to be helpful and replaced normal double quotes with those fancy and inappropriate ones.

You are right.
(my browser fonts don't show any difference, i should have copy past the text to some file... )

---

### Post by birddog165 on 2009-02-10
> **stroyan said:**
> The problem is not a lack of build-essential packages.
(Not yet, anyway.)

The problem is that you are using wierd unicode quote characters instead of proper ascii double quotes.
You have “Hello World\n”.
You need "Hello World\n".

I wonder if you used a text editor that tried to be helpful and replaced normal double quotes with those fancy and inappropriate ones.

Thank you so much

---

### Post by nehagupta on 2009-05-28
Hi i try to run a sample socket server proram
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
#define MYPORT 3490    /*the port users will be connecting to*/
#define BACKLOG 10     // how many pending connections queue will hold
void sigchld_handler(int s)
{
    while(wait(NULL) > 0);
}
int main(void)
{
    int sockfd, new_fd; // listen on sock_fd, new connection on new_fd
    struct sockaddr_in my_addr;    // my address information
    struct sockaddr_in their_addr; // connector&#8217;s address information
    int sin_size;
    struct sigaction sa;
    int yes=1;
    if ((sockfd = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
        perror("socket");
        exit(1);
    }
    if (setsockopt(sockfd,SOL_SOCKET,SO_REUSEADDR,&yes,sizeof(int)) == -1) {
        perror("setsockopt");
        exit(1);
    }
    my_addr.sin_family = AF_INET;         // host byte order
    my_addr.sin_port = htons(MYPORT);     // short, network byte order
    my_addr.sin_addr.s_addr = INADDR_ANY; // automatically fill with my IP
    memset(&(my_addr.sin_zero), &#8217;\0&#8217;, 8 ); // zero the rest of the struct
    if (bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr))== -1) {
        perror("bind");
        exit(1);
    }
    if (listen(sockfd, BACKLOG) == -1) {
        perror("listen");
        exit(1);
    }
    sa.sa_handler = sigchld_handler; // reap all dead processes
    sigemptyset(&sa.sa_mask);
    sa.sa_flags = SA_RESTART;
    if (sigaction(SIGCHLD, &sa, NULL) == -1) {
        perror("sigaction");
        exit(1);
    }
  while(1) { // main accept() loop
      sin_size = sizeof(struct sockaddr_in);
      if ((new_fd = accept(sockfd, (struct sockaddr *)&their_addr,
                                                     &sin_size)) == -1) {
          perror("accept");
          continue;
      }
      printf("server: got connection from %s\n",
                                         inet_ntoa(their_addr.sin_addr));
      if (!fork()) { // this is the child process
          close(sockfd); // child doesn&#8217;t need the listener
          if (send(new_fd, "Hello, world!\n", 14, 0) == -1)
              perror("send");
          close(new_fd);
          exit(0);
      }
      close(new_fd); // parent doesn&#8217;t need this
  }
  return 0;
}
and got error
/home/neetu/f.c: In function &#8216;main&#8217;:
/home/neetu/f.c:37: error: stray &#8216;\342&#8217; in program
/home/neetu/f.c:37: error: stray &#8216;\200&#8217; in program
/home/neetu/f.c:37: error: stray &#8216;\231&#8217; in program
/home/neetu/f.c:37: error: stray &#8216;\&#8217; in program
/home/neetu/f.c:37: error: stray &#8216;\342&#8217; in program
/home/neetu/f.c:37: error: stray &#8216;\200&#8217; in program
/home/neetu/f.c:37: error: stray &#8216;\231&#8217; in program
whats the issue

---

