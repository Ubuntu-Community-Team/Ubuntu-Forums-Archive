---
title: "Transfering large packets with sockets"
date: 2010-10-08
forum: Programming Talk
---

### Post by hosseinyounesi on 2010-10-08
Hi,

I want to use socket to transfer packets with size of 5000 bytes and more. I tried it with windows and I could transfer 4520 bytes (It seems 20 bytes is for TCP header). And with linux I can transfer smaller! Here is my code:

server:
```

struct sockaddr_in service;
service.sin_family = AF_INET;
service.sin_addr.s_addr = INADDR_ANY;
service.sin_port = htons( PORT );
SOCKET ListenSocket = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
bind(ListenSocket,(struct sockaddr*)&service,sizeof(service));
listen(ListenSocket, SOMAXCONN);
SOCKET Accepter;
while(true)
{
	Accepter = accept( ListenSocket, NULL, NULL );
	struct timeval tv;
	tv.tv_sec = 100;
	tv.tv_usec = 0;
	int buf_size=10*1000;
	if( setsockopt(Accepter,SOL_SOCKET,SO_RCVTIMEO,(char*)&tv,sizeof(tv))==-1 ||
		setsockopt(Accepter,SOL_SOCKET,SO_SNDTIMEO,(char*)&tv,sizeof(tv))==-1 ||
		setsockopt(Accepter,SOL_SOCKET,SO_SNDBUF,(char*)&buf_size,sizeof(int))==-1 ||
		setsockopt(Accepter,SOL_SOCKET,SO_RCVBUF,(char*)&buf_size,sizeof(int))==-1 )
	{
		int x=WSAGetLastError();
	}
	nt size=0;
	char tmp=1;

	if(recv(Accepter,(char*)&size,sizeof(size),0)==-1) {
		x=WSAGetLastError();
	}

	char *packet=new char[size];
	if(recv(Accepter,packet,size,0)==-1)
	{
		x=WSAGetLastError();
	}
	packet[size]=0;
}

```

client:
```

int sz=5000;
send(ConnectSocket,(char*)&sz,sizeof(sz),0);
char *sss=new char[sz];
string xx=base64_encode((unsigned char*)sss,sz);//to make it a string with no binary data
send(ConnectSocket,sss,sz,0);

```
setsockopt is done for client too.
It seems i'm missing something. I wrote the same code for C# and it worked.

Thanks b4

---

### Post by Zugzwang on 2010-10-08
What is actually your question? Why the TCP implementation in Linux doesn't allow sending such large chunks of data in one package?

Normally, if you are writing a TCP application, you would loop until you have received the data you wanted. This makes sure that you don't have to care about such issues.

---

### Post by hosseinyounesi on 2010-10-08
> Normally, if you are writing a TCP application, you would loop until you have received the data you wanted. This makes sure that you don't have to care about such issues.

Using a loop? Why? TCP, send and recv functions shall do it, but it seems that before receiving the entire message, recv returns! I want to know why recv acts like that?

---

### Post by worseisworser on 2010-10-08
Perhaps you're looking for *MSG_WAITALL*. See *[man 2 recv]("http://www.kernel.org/doc/man-pages/online/pages/man2/recv.2.html")*

---

### Post by dwhitney67 on 2010-10-08
> **hosseinyounesi said:**
> Using a loop? Why? TCP, send and recv functions shall do it, but it seems that before receiving the entire message, recv returns! I want to know why recv acts like that?

You managed to set the send/receive queue sizes for the client socket, but I do not believe this affects the MTU (Maximum Transmission Unit) supported by your router or your computer.  Many systems have this set to a value of 1400, or maybe 1500 (bytes).  Run 'ifconfig' for your ethernet adapter to see what it is set to, or examine your router settings.

What Zugzwang was recommending is that you employ code similar to the following:
```

int size = 0;

// receive size...

char* packet = new char[size];
int   recvd  = 0;

while (recvd != size)
{
   int bytes = recv(Acceptor, packet + recvd, size - recvd, 0);

   if (bytes == 0)
   {
      // client disconnected.
      break;
   }
   else if (bytes < 0)
   {
      if (errno == EAGAIN || errno == EINTR)
         continue;

      // else other error (probably fatal)
      break;
   }

   recvd += bytes;
}

if (recvd == size)
{
   // got a full message
}
else
{
   // some anomaly occurred
}

```

---

### Post by MadCow108 on 2010-10-08
you can use a/the TEMP_FAILURE_RETRY macro to avoid some loop code
[http://www.gnu.org/s/libc/manual/html_node/Interrupted-Primitives.html](http://www.gnu.org/s/libc/manual/html_node/Interrupted-Primitives.html)

only needed when you are not using _GNU_SOURCE

---

### Post by hosseinyounesi on 2010-10-09
Thanks you all,.
"MSG_WAITALL" worked for me :) But I want to set a timeout too. But I'm not sure that I have to use setsockopt with the SOCKET that is returned from with socket() function or accept(). 
Setting time out should be done in both server and client? with the same value?

I set time out only on server (with SOCKET that is returned from socket() function) and it worked BUT after the timeout, accept() function returns "EAGAIN" and does not accept any more connection!!!

> 
EAGAIN The socket is marked  non-blocking  and  the  receive  operation
              would  block,  or a receive timeout had been set and the timeout
              expired before data was received.


Is "EAGAIN" a FATAL error or I should just ignore it? Any way to disable it?

May I have some help?

Thanks

---

### Post by hosseinyounesi on 2010-10-09
I used setsockopt for the SOCKET returned from accept and now everything is working fine!

But let me know if there is any more issue.

Thanks

---

### Post by dwhitney67 on 2010-10-09
> **hosseinyounesi said:**
> ...
Is "EAGAIN" a FATAL error or I should just ignore it? Any way to disable it?

May I have some help?

Thanks

EAGAIN is not a fatal error; the description is exactly what you posted.  If you had paid careful attention to the code I posted earlier, you would have noticed that I looped back to the beginning of the while loop when such an event was detected.

If you prefer to use macros to obfuscate the behind-the-scenes workings of what transpires when a certain error condition arises, then that is fine.  But you should take the time to understand under which circumstances the recv() call could return an error, and whether or not you should ignore the error, or consider it to be something of interest.

---

### Post by hosseinyounesi on 2010-10-09
New problem!

There are many connections with TIME_WAIT state in netstat!
I shutdown and close the socket in both client and server and no error occurs. So, what's wrong?

[This link]("http://www.sunmanagers.org/pipermail/sunmanagers/2004-September/032709.html") is says that linux will make them to be in this state to use them again in future or I'm wrong?

Thanks b4

---

### Post by worseisworser on 2010-10-09
That's generally not a problem, hosseinyounesi.

The exception is (depending on context) when you want to restart a server that might have been killed abruptly; you'd want to set (*setsockopt*) the *SO_REUSEADDR* option then.

---

### Post by psusi on 2010-10-09
You seem to be a bit confused.  TCP is a stream oriented protocol, not packet oriented.  It does not transfer packets, it transfers streams of bytes.  If a single send() call takes 5000 bytes, that does not mean that it will send a 5000 byte packet ( and indeed, it generally won't ), nor does it mean the other end will get all 5000 bytes from recv().  You might have to call either send or recv several times to send or receive all 5000 bytes.

---

### Post by hosseinyounesi on 2010-10-10
SO_REUSEADDR didn't change anything. Connections are still in TIME_WAIT state :(
I used sleep(1) before shutting down and closing in server and now connections in client are in TIME_WAIT state and server is fine! That's really strange! The same example on Windows is working fine, So it seems that I'm missing something about Linux behavior!?

Any idea?

---

### Post by hosseinyounesi on 2010-10-10
Hi again,

I tried setting socket options on both client and server and still the same TIME_WAIT problem? What's wrong?!!! Number of connections in TIME_WAIT state just increases in server !!!!
shutting down and closing has been done, so why connections are still in that state?
I'm really really confused :( Client is Windows and server is Linux, Is that the problem?

Any idea?

---

### Post by worseisworser on 2010-10-10
Just Google TIME_WAIT and/or read about it in the Linux man-pages, hosseinyounesi; this stuff is not a problem.

---

### Post by hosseinyounesi on 2010-10-10
> this stuff is not a problem.

Number of connections in WAIT_STATE will increase more and the server will not be able to response to connections! SO IT IS A PROBLEM :(

---

### Post by worseisworser on 2010-10-10
Did you read the relevant Google hits and man-pages at all?

---

### Post by hosseinyounesi on 2010-10-10
Of course! I have a server that should be able to response to more than 10 connections per second, so increasing the connections in this state will make my server unable to respond after some hours. So it seems that there is a problem with closing and WAIT_TIME :(

---

### Post by psusi on 2010-10-10
> **hosseinyounesi said:**
> Of course! I have a server that should be able to response to more than 10 connections per second, so increasing the connections in this state will make my server unable to respond after some hours. So it seems that there is a problem with closing and WAIT_TIME :(

Then you didn't read the man page.  All connections go to TIME_WAIT after they are closed.  They TIME out and go away after a few minutes, hence the name of the state.

---

