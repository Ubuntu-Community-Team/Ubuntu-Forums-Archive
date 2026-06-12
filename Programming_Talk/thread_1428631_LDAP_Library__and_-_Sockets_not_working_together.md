---
title: "LDAP Library  and - Sockets not working together"
date: 2010-03-13
forum: Programming Talk
---

### Post by louieson on 2010-03-13
Dear all,
Along time ago a wrote a C daemon server program that communicates with clients. When a client first attaches the program it passes the users email credentials which where check against an IMAP server. When the IMAP server was retired I was only given the option to authenticate against LDAP. This worked very well for a number of years until we had to virtualize our servers. We used CENTOS, but when CENTOS patched its self it broke the VM. So we looked at Ubuntu 8.04 and it worked well under a VM environment. 
My daemon programmed complied with no warning (-Wall switch). But the clients could not connect. After much experimenting I reliased that if I linked in the ldap library it would not allow socket connections. 

Compile the program below first like this 
      cc t1.c -o t1 
and run it  (it will go into background) and connect to it using Telnet like so
   telnet 127.0.0.1  9446

The telnet program connects and after you type a string of greater that 10 charaters an hit return. The program will echo back the first 10 characters and terminate the telnet session.
kill the daemon with 
  killall t1

If you repeat the process but this time compile and link in ldap like so
     cc t1.c -o t1 -lldap

the program will compile correctly however when you run it and try to connect with telnet, telnet says that connect was closed by foreign host.

Any one got any ideas. All I have done is just linked in LDAP and it prevents any socket open for listening from working, and I have not even used ldap library calls in the code 

Regards

Louie

sample code below

//-------------------------------------------------------


#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <ctype.h>
#include <string.h>
#include <time.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <pwd.h>
#include <sys/time.h>
#include <errno.h>
#include <netdb.h>
#include <sys/stat.h>
#include <sys/uio.h>
#include <sys/wait.h>
#include <sys/un.h>


#define FALSE 0
#define TRUE !FALSE

char sendBuff[5000];

int server_sockfd, client_sockfd;
// added for updated system
struct sockaddr_in admin_address;
struct sockaddr_in temp_address;


int main(int argc,char **argv)
{
        int pid;
        int server_len,client_len;
        struct sockaddr_in server_address;
        struct sockaddr_in client_address;
        unsigned char *cptr;
        FILE *fp;
        int loop = 1;

        struct sockaddr_in loopback_address;


        if ((pid = fork()) == -1)
        {
                fprintf(stderr,"Unable to fork\n");
                exit(0);
        }

        if (pid)
                return 0;


        server_sockfd = socket(AF_INET, SOCK_STREAM, 0);
        server_address.sin_family=AF_INET;

//      server_address.sin_addr.s_addr = inet_addr("127.0.0.1");  // replaced to allow for admin client to communicate
        server_address.sin_addr.s_addr = htonl(INADDR_ANY);
    loopback_address.sin_addr.s_addr = inet_addr("127.0.0.1");

        server_address.sin_port = htons(9446);
        server_len = sizeof(server_address);
        bind(server_sockfd,(struct sockaddr *)&server_address,server_len);
        listen(server_sockfd,5);

        while (loop)
        {
        int j= 20;
                client_sockfd=(unsigned)accept(server_sockfd,
                                   (struct sockaddr *)&client_address,
                                   (unsigned *)&client_len);
                j = readn(client_sockfd,sendBuff,10);
//              readn(client_sockfd,sendBuff,2000);
                cptr=(unsigned char *)sendBuff;

                temp_address.sin_addr.s_addr = client_address.sin_addr.s_addr;

                printf("%s\n",sendBuff);

                readn(client_sockfd,"ABCDEFHIJKLMNOPQRSTUVWXYZ",20);

                close(client_sockfd);
        }
        return 0;
}


int writen(int fd, void *vptr, int n)
{
        int nleft;
        int nwritten;
        char *ptr;

        ptr = vptr;
        nleft = n;

        while (nleft > 0)
        {
                if ((nwritten = write(fd,ptr,nleft)) <=0)
                {
                        if (errno == EINTR)
                                nwritten = 0;
                        else
                                return -1;
                }
                nleft -=nwritten;
                ptr+= nwritten;
        }
        return (n);
}

int readn(int fd, void *vptr, int n)
{
        int nleft;
        int  nread;
        char *ptr;

        ptr = vptr;
        nleft = n;

        while (nleft > 0)
        {
                if ((nread = read(fd,ptr,nleft)) < 0)
                {
                        if (errno == EINTR)
                                nread = 0;
                        else
                                return -1;
                }
                else if (nread == 0)
                        break;
                nleft -=nread;
                ptr+= nread;
        }
        return (n- nleft);
}

---

### Post by dwhitney67 on 2010-03-13
This seems odd:
```

readn(client_sockfd,"ABCDEFHIJKLMNOPQRSTUVWXYZ",20 );

```
Should you not be using writen()?

As for the the LDAP library (libldap.so), it has no bearing on your application.  As you have pointed out, you are not referencing it whatsoever in your code.

The reason why your telnet session (or client app) is getting the "Connection closed by foreign host" message is that you summarily close the client's socket after the (erroneous) readn() call described above.

You should not disconnect the client, unless that is a 'feature' of your application you would like to preserve.  Allow for the client to disconnect in their own time.  Your server app (daemon) will know when a client disconnects when the read() function returns zero bytes.  Because you somewhat hide this information with readn's return value, it's not easily obvious.  Consider refactoring your readn() to be something like:
-------------------------------
EDIT:  Ignore the code below; there is a bug in it.  Refer to my later post for the corrected version.
-------------------------------
```

int readn(int fd, char* buf, const int numBytes)
{
   int bytesRead = 0;

   while (bytesRead < numBytes)
   {
      int rtn = read(fd, buf + bytesRead, numBytes - bytesRead);

      if (rtn < 0 && errno != EAGAIN)
      {
         return rtn;        // error
      }
      else if (rtn == 0)
      {
         break;             // client disconnected
      }

      if (rtn > 0)
      {
         bytesRead += rtn;
      }
   }

   return bytesRead;
}

```

If you still have questions, post back here.

P.S.  In the future, please post your code using CODE tags.  A handy button is available in the upper right hand side of the editor pane.

---

### Post by louieson on 2010-03-14
Thanks for your reply, The program I enclosed is just a cut and paste of a  small section of a 20,000 line program that has been running on Centos, Fedora for years and about 2 years went I started linking in the LDAP library for authenication.  But under Ubuntu if I go back to my IMAP authenication version without linking LDAP it works, but my IMAP version does not work when I do link in the LDAP library (and this program contains no LDAP system calls). I know it sound crazy but linking LDAP on unbuntu for may program break socket code that works without the LDAP library. I have a hard time believing it my self but every thing I do (test code) leads me to this conclusion
 
The second readn was not neccesarym(it was a writen at on stage)  and can be left out of the program. Only the first readn
j = readn(client_sockfd,sendBuff,10);
(remove all other readn)

is required so when you telnet to the daemon it blocks until you provide 10 characters. If you compile the code with no ldap library telnet does not immidately terminate. If you do link in ldap the connection with telnet terminates immediately. Try it because its driving me crazy
 
Any way thanks for your time
 
Regards
Louie

---

### Post by dwhitney67 on 2010-03-14
Earlier, I did try your code!  I know where the issues lie; I also know that LDAP is not a factor.

With the second readln() commented out (ie the one that outputs the alphabet), your program runs as designed.

So since I am not able to produce any other anomalies, I would say that the code you posted is not the cause of your application's issue(s); maybe it lies elsewhere within the 20 KSLOC that you mentioned.

---

### Post by dwhitney67 on 2010-03-14
I did a little more investigation, and I found that when testing with telnet, both a carriage-return and newline character is appended to anything the user sends.

This issue may be throwing off your results.  I would recommend that you utilize a different client application for sending data, or consider setting up your client's socket as non-blocking and relying on select() to determine when there is data to be read.

I also discovered that the modified readn() implementation I provided earlier had a bug in it; so I hope that you did not spend any time using it.

Here's a (modified) listing of your code, which now works (regardless if linked with LDAP):
```

#include <sys/socket.h>
#include <netinet/in.h>
#include <fcntl.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>


#define FALSE 0
#define TRUE  !FALSE

void serviceClient(int fd);
int  readn(int fd, char* buf, const int numBytes);

int main(int argc, char** argv)
{
   int pid = -1;

   if ((pid = fork()) == -1)
   {
      fprintf(stderr, "Unable to fork\n");
      return errno;
   }

   if (pid)
   {
      // parent
      return 0;
   }

   // daemon continues...
   int server_sockfd = socket(AF_INET, SOCK_STREAM, 0);

   struct sockaddr_in server_address;

   memset(&server_address, 0, sizeof(server_address));

   server_address.sin_family      = AF_INET;
   server_address.sin_addr.s_addr = htonl(INADDR_ANY);
   server_address.sin_port        = htons(9446);

   int status = bind(server_sockfd, (struct sockaddr*) &server_address, sizeof(server_address));

   if (status != 0)
   {
      fprintf(stderr, "failed to bind.\n");
      return errno;
   }

   listen(server_sockfd, 5);

   int loop = TRUE;

   while (loop)
   {
      int client_sockfd = accept(server_sockfd, 0, 0);

      if (client_sockfd)
      {
         serviceClient(client_sockfd);
         close(client_sockfd);
      }
   }

   return 0;
}

void serviceClient(int fd)
{
   int  clientConnected = TRUE;
   char rcvBuf[11] = {0};

   // setup client socket to be non-blocking
   int flags = fcntl(fd, F_GETFL, 0);
   fcntl(fd, F_SETFL, flags | O_NONBLOCK);

   fd_set save_fds;
   FD_ZERO(&save_fds);
   FD_SET(fd, &save_fds);

   while (clientConnected)
   {
      fd_set read_fds = save_fds;

      int sel = select(fd + 1, &read_fds, 0, 0, 0);

      if (sel > 0)
      {
         memset(rcvBuf, 0, sizeof(rcvBuf));

         int bytesRead = readn(fd, rcvBuf, sizeof(rcvBuf) - 1);

         if (bytesRead == 0)
         {
            fprintf(stdout, "client disconnected.\n");

            clientConnected = FALSE;
         }
         else if (bytesRead > 0)
         {
            fprintf(stdout, "%s", rcvBuf);
         }
      }
   }
}

int readn(int fd, char* buf, const int numBytes)
{
   int bytesRead = read(fd, buf, numBytes);

   if (bytesRead < 0 && errno != EAGAIN)
   {
      fprintf(stderr, "Error reading from socket (%d).\n", fd);
   }

   return bytesRead;
}

```

P.S.  I left out the writen() function; you can add it back if needed.

---

### Post by louieson on 2010-03-14
Thanks for the code. I tried it firstly without using the ldap libraries
 
cc uf1.c -o uf1
 
It work as expected when I connected to it via telnet.
 
Then I tried 
 
 cc uf1.c -o uf1  -lldap
 
and when I connected to it using telnet I got
 
telnet 127.0.0.1
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

I hate to say it but  even your code does not work when ldap library is linked in as I expected.
 
I know the socket is open for listening because lsof -i tells me so
 
I am running Ubuntu 8.04 full patched with ldap library libldap-2.4-2 I have tried this on a virtualised and unvirtualised machine with the same result.
 
Again I am stumped, I have never come across this issue in 25 years of programming under *nix.  I may build my own library from openldap to see if that fixes the issue.
 
Thanx for your time.
 
Regards
Louie
 
PS the program that I am trying to move to Ubuntu is part of a Tutorial Enrolment System that is hit by alot of students at once. When the system just opens for enrolments , there are upwards of 8000+ socket connects on the server for over 60 minutes as student select tutorials. So the code is very robust (never crashed under this load), and the code uses GDBM database for storage, and the server never gets over 15% CPU usage during enrolment phase.  Basically I am trying to say that it is not a programming issue as this would have been detected year ago through program crashes, but this have never occurred.

---

### Post by dwhitney67 on 2010-03-14
> **louieson said:**
>  
and when I connected to it using telnet I got
 
telnet 127.0.0.1
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

Are you sure the command above is what you tried?? If so, of course telnet failed.  Try again, but this time specify the port number (9446).

P.S.  After you run the daemon process, attach to it using 'strace' to see where it is at in it's execution.  You will need the PID of your daemon; once you know it, running 'strace' is as follows:
```

strace -p <pid>

```

---

