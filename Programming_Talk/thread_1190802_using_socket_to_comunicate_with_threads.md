---
title: "using socket to comunicate with threads"
date: 2009-06-18
forum: Programming Talk
---

### Post by matrix4ever on 2009-06-18
I made a rock-paper-scissors game implemented with threads plying randomly using a file. The game works perfectly but I also need to send a message to the threads which says the result of the last match they played. So I cut off all the lines which aren't relevant and I hope someone will make this code work. (I can't post the entire code because this is a college project and there are many persons who would like to simply copy it by googleing and then changing a bit - I also tried it). 

So now the problem is just "how can I send a string to a thread using sockets?" with this condition:
-function play executes some instructions and then calls the function judge, which (after judging) should send to the thread a string.

When I execute the code I get this:
ivo@ivo-laptop:~$ socket
STATUS: thread starts
STATUS: server declared
STATUS: socket syscall
connection with server failed: Connection refused

**CODE:**
// not quite sure that all of these are needed but it doesn't matter
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <pthread.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <ctype.h>
#include <sys/times.h>

#define SERVER_PORT 1313
#define MAXLENGTH 30

void play(void);
void judge(void);

int sock, client_len, fd;

main() {

  pthread_t thread1,thread2;

  struct sockaddr_in server;
  /* setting transport end point */
  if((sock = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
    perror("system call socket failed");
    exit(1);
  }
  server.sin_family = AF_INET;
  server.sin_addr.s_addr = htonl(INADDR_ANY);
  server.sin_port = htons(SERVER_PORT);
  /* binding address to transport end point */
  if (bind(sock, (struct sockaddr *)&server, sizeof server) == -1) {
    perror("system call socket failed");
    exit(2);
  }

  // "client" threads creation
  if(pthread_create(&thread1,NULL,(void *)&play,NULL)!=0) {
    perror("Errore nella creazione del primo thread");
    exit(2);
  }
/*
  if(pthread_create(&thread2,NULL,(void *)&play,NULL)!=0) {
    perror("Errore nella creazione del secondo thread");
    exit(3);
  }
*/
  // waiting for threads to terminate
  pthread_join(thread1,NULL);
//  pthread_join(thread2,NULL);

}

void play(void){
printf("STATUS: thread starts\n"); // test line
  // creazione socket per ricezione
  int sockfd;
  struct sockaddr_in server={AF_INET,htons(SERVER_PORT),INADDR_ANY};
printf("STATUS: server declared\n");  // test line
  int i=0,len;
  char buf[MAXLENGTH],c;
  if((sockfd = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
    perror("system call socket failed");
  exit(1);
  }
printf("STATUS: socket syscall\n");  // test line
  /* connecting to server */
  if(connect(sockfd,(struct sockaddr *)&server,sizeof server)==-1) {
    perror("connection with server failed");
    exit(2);
  }
printf("STATUS: connected\n");   // test line (which currently doesn't show)
  judge();
  // getting the message
  if(recv(sockfd,buf,len,0)>0) {
    printf("%s\n",buf);
  }
  else {
    perror("connection with server interrupted");
    exit(3);
  }
  /* closing the connection */
  close(sockfd);
}

void judge(void){
struct sockaddr_in client;
  /* managing clients connetions */
  while (1) {
    client_len = sizeof(client);
    if ((fd = accept(sock, (struct sockaddr *)&client, &client_len)) < 0) {
      perror("accepting connection");
      exit(3);
    }
    send(fd, "* This will be printed by the thread if this program works*\n" , MAXLENGTH, 0);
    close(fd);
  }

}
**END OF CODE**

Thanx to all people who will try to solve this problem

---

### Post by dwhitney67 on 2009-06-18
To send a string through a socket is actually quite easy:

```

int rtn = send(sd, str, strlen(str), 0);

```
where sd is obtained from either socket() (when the client is sending) or accept() (when the server is sending); str is a (const) char*.

You may want to verify that the string is sent by checking the rtn value.


P.S.  In the future, please post your code using the CODE-tags... similar to above.

---

