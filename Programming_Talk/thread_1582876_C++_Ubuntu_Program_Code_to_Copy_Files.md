---
title: "C++ Ubuntu Program Code to Copy Files"
date: 2010-09-27
forum: Programming Talk
---

### Post by Geek10 on 2010-09-27
Hi all,

I am writing a c++ program to move a file across a network. The file  size is a few hundred kilobytes. The network is wireless but gets speeds  of up to 100MBps. I am fairly inexperienced with C++ programming, but  am very willing to do the hard yards and learn!

I have tried searching the internet, but got surprisingly little help  for code to copy files across the network (it would always gather  command line instructions, not how to code it in C++).

So my code so far is this:
[PHP]
#include <iostream>

using namespace std;

int main(){
    cout << "About to copy files. \n";
    cp( C:\test.txt, C:\newdirectory\test.txt);
    return 0;
}
[/PHP]My makefile is:
[PHP]
# Created: 27/9/10 - MBaulis
# Purpose: Make program to move files over network

CC=gcc
CXX=g++

LDFLAGS=-pthread 
LIBS= -lrt

IFLAGS=

copyover_SOURCES=$(wildcard src/*.cpp)
copyover_HEADERS=$(wildcard src/*.h)
#copyover_OBJECTS=$(copyover_SOURCES:.cpp=.o)

FileTransfer: $(copyover_SOURCES) $(copyover_HEADERS)
    
    $(CXX) -g3 $(LDFLAGS) -o $@ $(IFLAGS) $^ $(LIBS)
[/PHP]The PHP seems to struggle at the /*.

So the whole lot is here:

# Created: 27/9/10 - MBaulis
# Purpose: Make program to move files over network

CC=gcc
CXX=g++

LDFLAGS=-pthread 
LIBS= -lrt

IFLAGS=

copyover_SOURCES=$(wildcard src/*.cpp)
copyover_HEADERS=$(wildcard src/*.h)
#copyover_OBJECTS=$(copyover_SOURCES:.cpp=.o)

FileTransfer: $(copyover_SOURCES) $(copyover_HEADERS)
    
    $(CXX) -g3 $(LDFLAGS) -o $@ $(IFLAGS) $^ $(LIBS)


I'll post my errors in the next post, I have a technical difficulty at the moment.

Does anyone have any suggestions about how to do this?

Thanks, Geek10.

---

### Post by dwhitney67 on 2010-09-27
> **Geek10 said:**
> 
So my code so far is this:
[PHP]
#include <iostream>

using namespace std;

int main(){
    cout << "About to copy files. \n";
    cp( C:\test.txt, C:\newdirectory\test.txt);
    return 0;
}


If this is all you have, then you have a long way to go.  Personally I'm not aware of a cp() function in either the C or C++ libraries.  So unless you have invented a magical function (and it appears you haven't), I don't see what you shown above to be compilable (and that is aside from the syntax errors).

If you do not know C++, then I suggest you learn it properly.  Of course, if you want to use the command-line solution within a C++ program, you could always rely on the system() library function in which you call scp (secure copy).

P.S.  Use CODE tags for code; not PHP tags.

---

### Post by ipatfrmww on 2010-09-27
Here is a little piece of code I found, it sends a message from one user to the other, you could probably adapt it for your purposes. Its in c, and as far as I am aware it is pretty system specific(and yes I saw that C: ) but its a start.
Although I would suspect that there is an actual library you can use instead that does the job the proper way(there always is).
Note, I didn't write these, so no criticism please for their lack of conformity to various standards.
The server:
```

/* A simple server in the internet domain using TCP
   The port number is passed as an argument */
#include <stdio.h>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>

void error(char *msg)
{
    perror(msg);
    exit(1);
}

int main(int argc, char *argv[])
{
     int sockfd, newsockfd, portno, clilen;
     char buffer[256];
     struct sockaddr_in serv_addr, cli_addr;
     int n;
     if (argc < 2) {
         fprintf(stderr,"ERROR, no port provided\n");
         exit(1);
     }
     sockfd = socket(AF_INET, SOCK_STREAM, 0);
     if (sockfd < 0) 
        error("ERROR opening socket");
     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);
     if (bind(sockfd, (struct sockaddr *) &serv_addr,
              sizeof(serv_addr)) < 0) 
              error("ERROR on binding");
     listen(sockfd,5);
     clilen = sizeof(cli_addr);
     newsockfd = accept(sockfd, 
                 (struct sockaddr *) &cli_addr, 
                 &clilen);
     if (newsockfd < 0) 
          error("ERROR on accept");
     bzero(buffer,256);
     n = read(newsockfd,buffer,255);
     if (n < 0) error("ERROR reading from socket");
     printf("Here is the message: %s\n",buffer);
     n = write(newsockfd,"I got your message",18);
     if (n < 0) error("ERROR writing to socket");
     return 0; 
}
```and the client:
```

#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h> 

void error(char *msg)
{
    perror(msg);
    exit(0);
}

int main(int argc, char *argv[])
{
    int sockfd, portno, n;
    struct sockaddr_in serv_addr;
    struct hostent *server;

    char buffer[256];
    if (argc < 3) {
       fprintf(stderr,"usage %s hostname port\n", argv[0]);
       exit(0);
    }
    portno = atoi(argv[2]);
    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    if (sockfd < 0) 
        error("ERROR opening socket");
    server = gethostbyname(argv[1]);
    if (server == NULL) {
        fprintf(stderr,"ERROR, no such host\n");
        exit(0);
    }
    bzero((char *) &serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    bcopy((char *)server->h_addr, 
         (char *)&serv_addr.sin_addr.s_addr,
         server->h_length);
    serv_addr.sin_port = htons(portno);
    if (connect(sockfd,&serv_addr,sizeof(serv_addr)) < 0) 
        error("ERROR connecting");
    printf("Please enter the message: ");
    bzero(buffer,256);
    fgets(buffer,255,stdin);
    n = write(sockfd,buffer,strlen(buffer));
    if (n < 0) 
         error("ERROR writing to socket");
    bzero(buffer,256);
    n = read(sockfd,buffer,255);
    if (n < 0) 
         error("ERROR reading from socket");
    printf("%s\n",buffer);
    return 0;
}
```compile as such:
gcc -o server server.c
gcc -o client client.c

then run (in 2 different terminals or computers or countries or whatever)
./server 3000
then 
./client 127.0.0.1 3000

replace 127.0.0.1 with the ip, and 3000 with the port

---

### Post by Geek10 on 2010-09-27
> **dwhitney67 said:**
> If this is all you have, then you have a long way to go.
Hehe...:) Indeed I do. That's why I came to get some help.

> **dwhitney67 said:**
> Personally I'm not aware of a cp() function in either the C or C++ libraries.  So unless you have invented a magical function (and it appears you haven't), I don't see what you shown above to be compilable (and that is aside from the syntax errors).

Yes, my original code was wrong. I am now trying to use:
```

system(cp "\test.txt" "\tmp\test.txt");

```Do you think that is more like it?

A friend suggested I use a shell script or else the system commands. Eventually I want to run this code in a larger C++ file which I have coded (about a couple of a hundred line long), but I just want to get the Ubuntu specific moving and manipulating of the files happening without errors for Ubuntu before I stick it in this larger problem. You see, my hundreds of line of other code works fine on Windows, and Ubuntu, but I know that the moving the files is much more Ubuntu specific, and I have hardly used Unix systems before.


> **dwhitney67 said:**
> If you do not know C++, then I suggest you learn it properly.  Of course, if you want to use the command-line solution within a C++ program, you could always rely on the system() library function in which you call scp (secure copy).
Good point. scp sounds good. I'll look into that.

> **dwhitney67 said:**
> P.S.  Use CODE tags for code; not PHP tags.
Ok. Thanks for that. I thought colours might make the code clearer - it certainly does for me, but then I'm a beginner-level programmer!

Thanks for your help!

And ipatfrmww, thanks for your contribution too. Even though it's C, I might still be able to take some suggestions from it's technique.

---

### Post by Geek10 on 2010-09-27
Hi all,

I am trying to write some C++ code to copy a file over the network. The basic rundown is this:
1. Look in particular directory of folder across network (normally I use ssh@10.42.##.# to do this).
2. There will be a number of files there, all with the name "image_00###" and "text.txt". I want to get the latest ones of these.
3. Copy these two latest files over the network to a folder on my computer.
4. Delete all of the previous versions of the files.

I am not an experienced programmer, but I'll put in the hard yards to learn. However, I've found that little tips from experienced programmers have sometimes saved me DAYS of searching, so I'm always thankful for help.

What I have done so far is this:
```

#include <stdlib.h>

int main(){

    system(cp /test.txt /tmp/test.txt);

    return 0;
}

```The errors I get when I use the command "make" are:

g++ -g3 -pthread  -o FileTransfer  src/CopyOverNetwk.cpp -lrt
src/CopyOverNetwk.cpp: In function âint main()â:
src/CopyOverNetwk.cpp:5: error: âcpâ was not declared in this scope
src/CopyOverNetwk.cpp:5: error: âtestâ was not declared in this scope
src/CopyOverNetwk.cpp:5: error: âtmpâ was not declared in this scope
make: *** [FileTransfer] Error 1

I typed in cp /test.txt /tmp/test.txt into my Ubuntu terminal, and that worked. So I know that's not the problem. It seems like I need the library that includes "cp".

In my research to try and find a solution, I found this on the Ubuntu forums:

Whenever you feel the need to interact with some external application using system(),   
1. First research whether a library can do the same.  
2. If there's none, use popen().   
3. If popen() isn't possible, use system() or implement it yourself.

So it seems like I might be going about my problem the wrong way.

I also found out that calling a shell script from C++ code might be the other way, with example code below:
```

#include (what to include unfortunately wasn't provided)

main(){
     if(fork()==0){
           execl("/bin/sh", "/home/oracle/temp/hello.sh", "hello.sh", NULL);
     }
}

```Does anyone have any suggestions. Absolutely anything would help, especially what commands to use, and if you are feeling really generous, a bit of code would be vastly appreciated!

Thanks

---

### Post by Geek10 on 2010-09-27
So I have solved the copying problem by putting quotations around the command.
```

#include <stdlib.h>

int main(){

    system("cp /test.txt /tmp/test.txt");

    return 0;
}

```

Any suggestions on copying the latest file in a folder over?

---

### Post by bodhi.zazen on 2010-09-28
> **Geek10 said:**
> So I have solved the copying problem by putting quotations around the command.
```

#include <stdlib.h>

int main(){

    system("cp /test.txt /tmp/test.txt");

    return 0;
}

```Any suggestions on copying the latest file in a folder over?

I merged your two threads. Please do not start multiple threads on the same topic.

---

### Post by Geek10 on 2010-09-28
Ok. Sorry about that. I thought I would start a new one since I was more advanced, but I'm continuing to learn forum etiquette!

---

