---
title: "Sending data - line by line?"
date: 2009-02-22
forum: Programming Talk
---

### Post by tuckker on 2009-02-22
I'm a Java programmer, but I'm starting to learn C programming language. Hope someone can help me here...

My server side socket is coded using Java, and the client side is coded through C. I can telnet to the Java app and the Java app shows that the input is being received from telnet. 

However, when I use my C program to connect to the Java app, it shows that they are connected, but the Java app couldn't receive any input from the C program.

Someone told me that I need to check if the way of the C Program is sending the data is "compatible" with my Java app, but since i'm new to C, I hope someone could do a quick go through my C source below.

My Java app receives input character by character, as shown in below code:

Part of ServerThread.cpp
```
..
try {
            if (socket.isConnected()) {
                System.out.println("Server is connected to IP: " + socket.getInetAddress() + " Port: " + socket.getPort() + "");
            }
 
            // Get data from remote device
            BufferedReader in = new BufferedReader(
                    new InputStreamReader(
                    socket.getInputStream()));
 
            
            try {
                while (true) {
                    int i = in.read();
                    if (i == -1) {
                        break;
                    }
                    char c = (char) i;
                    System.out.print(c);
                }
                
            } catch (IOException e) {
                System.err.println(e);
            }
```

However, on my client side, it's a C program, and sending through:

Part of main.cpp
```
//-----------------------------------------------------------------//
// Function: SendMessage()
// Input Params:
//    *Message : string with the message to send.
// Output Params:
// Description:
//    Sends the message using TCP or UDP socket.
//-----------------------------------------------------------------//
VOID SendMessage( CHAR *Message )
{
   INT  ReturnCode;
 
#ifdef TCP
   ReturnCode = TCP_SendData((CHAR *)IPaddr, dest_port, Message, strlen(Message));
   if(RemoteServerDisconnected || (ReturnCode == -1)) {
       Status = STOP_INET_STATE;
   }else {
      WriteTraces("TCP-> All data are sent");
   }
#else
   ReturnCode = UDP_SendData((CHAR *) IPaddr, dest_port, Message, strlen( Message));
   if(ReturnCode == -1) {
      ConnectionError = TRUE;
   } else {
      WriteTraces("UDP-> All data are sent");
   }
#endif
}
```

Part of socket.cpp
```
//-----------------------------------------------------------------//
// Function: TCP_SendData()
// Input Params:
// Output Params:
// Description:
//-----------------------------------------------------------------//
INT TCP_SendData( CHAR *ip, INT port, CHAR *buffer, INT buffer_length )
{
   struct sockaddr_in  server;
   struct hostent      *hp;
   INT                 SocketFD;
   struct timeval      timeout;
   INT                 error;
   INT                 sent_bytes = 0;
   INT                 total_bytes = 0;
   INT                 tries;

   WriteTraces("\nSOCKET->TCP: TCP_SendData() start\n");

	//Time outs on socket operations
   timeout.tv_sec = 5;
   timeout.tv_usec = 0;

//   sigpipe_signal.sa_handler = sigpipe_handler;
//   sigpipe_signal.sa_flags = 0;
//   sigaction(SIGPIPE, &sigpipe_signal, &sigpipe_signalOld);

   // Obtain host data
   if ((hp = gethostbyname ((CHAR*)ip)) == 0) {
      perror("gethostbyname() failed");
      return -1;
   }
   else { // We can resolve the host so we continue
      memset((CHAR*)&server, 0, sizeof(server));
      // Construct the server address structure
      server.sin_family = AF_INET;
      server.sin_addr.s_addr = ((struct in_addr *)(hp->h_addr))->s_addr;
      server.sin_port = htons(port);

      //Obtain socket
      if ((SocketFD = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
         perror("socket() failed");
         return -1;
      }
/*
      //Set time-out parameters
      if (setsockopt(SocketFD, SOL_SOCKET, SO_SNDTIMEO, &timeout, sizeof(timeout)) == -1) {
		   perror("setsockopt() failed");
         close(SocketFD);
         return -1;
      }
		if (setsockopt(SocketFD, SOL_SOCKET, SO_RCVTIMEO, &timeout, sizeof(timeout)) == -1) {
		   perror("setsockopt() failed");
         close(SocketFD);
         return -1;
      }
*/

      // Set non-blocking for the socket
      if (fcntl(SocketFD, F_SETFL, O_NONBLOCK)) {
         printf("SOCKET->TCP Error making socket file descriptor non blocking\n");
         close(SocketFD);
         return -1;
      }

      WriteTraces("SOCKET->TCP: connecting to the server");

      // Conect with specified port of the server.
      // If the connection cannot be established immediately and O_NONBLOCK is set
      // for the file descriptor for the socket, connect() shall fail and set errno
      // to [EINPROGRESS], but the connection request shall not be aborted.
      // Subsequent calls to connect() for the same socket, before the connection is
      // established, shall fail and set errno to [EALREADY].
      do {
         error = connect(SocketFD, (struct sockaddr*)&server, sizeof(server));
         if ((error == -1) && (errno != EINPROGRESS) && (errno != EALREADY) && (errno != EAGAIN)) {
//         printf("connect:%s %d\n", strerror(errno), errno);
            perror("connect() failed");
            close(SocketFD);
            return -1;
         }
      }while(error != 0);

/*
      // Uncomment the following lines in case of Blocking socket.
      // Connect with specified port of the server
      if (connect(SocketFD, (struct sockaddr*)&server, sizeof(server)) == -1) {
         printf("connect: %s %d\n", strerror(errno), errno);
         close(SocketFD);
         perror("connect() failed");
         return -1;
      }
*/
      WriteTraces("SOCKET->TCP: socket connected");

      tcp_fd = SocketFD;
      TCP_StartRXThread();
      (*Fncusecsleep)(1, 0);

		//Send message to the server
		do {
         WriteTraces("\nSOCKET->TCP: sending %s, %d bytes\n", buffer, buffer_length);

			sent_bytes = sendto(SocketFD, buffer + total_bytes, buffer_length - total_bytes, 0,
						(struct sockaddr *)&server, sizeof(server));
			if (sent_bytes == -1) {
            TCP_StopRXThread();
				close(SocketFD);
				return -1;
			}
			total_bytes += sent_bytes;
		} while(total_bytes < buffer_length);
      WriteTraces("SOCKET->TCP: send message OK");

      //Get an answer from the server
      tries = 0;
      do {
         pthread_mutex_lock(&RxLock);
         if (!rx_data_received && (tries != 1)) {
            pthread_mutex_unlock(&RxLock);
            (*Fncusecsleep)(1, 0);
         }
         else {
            if(rx_data_received) {
               pthread_mutex_unlock(&RxLock);
               break;
            }
            else
               pthread_mutex_unlock(&RxLock);
         }
      }while(tries++ < 120); // If no answer from the server wait for 2 minutes

      TCP_StopRXThread();
      close(SocketFD);
   }

//   remoteHostDisc = FALSE;
   WriteTraces("SOCKET->TCP: TCP_SendData() end");
   return 0;
}
```

Any idea what's the problem?

---

### Post by The Cog on 2009-02-23
My first guess is that you are not sending a line ending \n at the end of the message. I know readLine() needs to see a line ending but I can't remember clearly about just read() - probably not on second thoughts.

My second guess is that you are not calling socket.flush() after sending the message, so it is still sitting in the clients transmit buffer.

---

### Post by dwhitney67 on 2009-02-23
I could help, but since you wrote your code in M$ C, it's kind of hard to follow everything.  Also, the program is not very modular.

Try to keep things simple.  Your client needs to do the following:
[INDENT]1.  Open a socket
2.  Connect the server using a hostname and port number
3.  Send message(s)[/INDENT]

I assume from your post that you are attempting to use TCP.  Therefore your application does not have to repeat step 2 each time you want to send a message.

If you are using UDP, you skip step 2 in its entirety.

Below is some code I threw together that you can use to set up a socket, connect to a server, and send a message (all for TCP).  I strongly suggest that you define these functions in a header file, and then place the implementation in a .c file.  Translate to M$ C if needed.

TCPSocket.h
```

#ifndef TCP_SOCKET_H
#define TCP_SOCKET_H

// Both Server and Client operation(s)
//
int CreateSocket();

int Send(int sd, const char* msg, const unsigned int msgSize);

int Recv(int sd, char* buf, const unsigned int bufSize);

void CloseSocket();

int ReuseSocket(int sd, int enable);


// Server operation(s)
//
int Bind(int sd, const char* address, const unsigned short port);

int Listen(int sd, unsigned int backlog);

int Accept(int sd);


// Client operation(s)
//
int Connect(int sd, const char* address, const unsigned short port);

#endif

```

TCPSocket.c:
```

#include "TCPSocket.h"
#include <netdb.h>
#include <errno.h>
#include <unistd.h>
#include <string.h>


int FillAddress(const const char* address, const unsigned short port, struct sockaddr_in* addr);


// Both Server and Client operation(s)
//
int CreateSocket()
{
  return socket(AF_INET, SOCK_STREAM, 0);
}

int Send(int sd, const char* msg, const unsigned int msgSize)
{
  unsigned int bytesSent = 0;

  while (bytesSent != msgSize)
  {
    int rtn = send(sd, msg + bytesSent, msgSize - bytesSent, 0);

    if (rtn < 0 && errno == EAGAIN)
    {
      continue;
    }
    if (rtn < 0)
    {
      return -1;
    }

    bytesSent += rtn;
  }

  return (int)bytesSent;
}

int Recv(int sd, char* buf, const unsigned int bufSize)
{
  int rcvdBytes = 0;

  if ((rcvdBytes = recv(sd, buf, bufSize, 0)) < 0 && errno != EAGAIN)
  {
    return -1;
  }

  return rcvdBytes;
}

void CloseSocket(int sd)
{
  close(sd);
}

int ReuseSocket(int sd, int enable)
{
  const unsigned int optLen = sizeof(int);

  return setsockopt(sd, SOL_SOCKET, SO_REUSEADDR, (void*) &enable, optLen);
}


// Server operation(s)
//
int Bind(int sd, const char* address, const unsigned short port)
{
  struct sockaddr_in addr;

  FillAddress(address, port, &addr);

  return bind(sd, (struct sockaddr*) &addr, sizeof(struct sockaddr_in));
}

int Listen(int sd, unsigned int backlog)
{
  return listen(sd, backlog);
}

int Accept(int sd)
{
  return accept(sd, 0, 0);
}


// Client operation(s)
//
int Connect(int sd, const char* address, const unsigned short port)
{
  struct sockaddr_in destAddr;

  FillAddress(address, port, &destAddr);

  return connect(sd, (struct sockaddr*) &destAddr, sizeof(destAddr));
}


// Miscellaneous private operations
//
int FillAddress(const const char* address, const unsigned short port, struct sockaddr_in* addr)
{
  struct addrinfo* host_info = 0;

  if (getaddrinfo(address, 0, 0, &host_info) != 0  ||
      !host_info || !host_info->ai_addr || host_info->ai_family != AF_INET)
  {
    if (host_info) freeaddrinfo(host_info);
    return -1;
  }

  memcpy(addr, host_info->ai_addr, sizeof(struct sockaddr_in));
  addr->sin_port = htons(port);

  freeaddrinfo(host_info);

  return 0;
}

```

This reduces your Client application to:
```

#include "TCPSocket.h"
#include <stdio.h>
#include <stdbool.h>
#include <string.h>
#include <unistd.h>


int main(int argc, char** argv)
{
  int sd = CreateSocket();

  if (sd > 0 && Connect(sd, "localhost", 9000) == 0)
  {
    const char* msg = "Hello Server\n";
    char buf[256] = {0};

    Send(sd, msg, strlen(msg));

    if (Recv(sd, buf, sizeof(buf) - 1) > 0)
    {
      printf("received server response: %s\n", buf);
    }

    CloseSocket(sd);
  }
  else
  {
    printf("failed to create socket and/or connect.\n");
  }

  return 0;
}

```
Of course, more error checking could be done, but hopefully you get the gist.

P.S.  Change the server address and port number in the program above.  Also, for the message sent, a new line is included in the message; that is because the server I tested with expected it.  If you are sending fixed-length messages, or if your client/server have a unique messaging protocol, then you may not need the newline.

---

