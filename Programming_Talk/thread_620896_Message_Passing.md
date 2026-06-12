---
title: "Message Passing"
date: 2007-11-23
forum: Programming Talk
---

### Post by earendil1234 on 2007-11-23
Hi,

I used QNX before for writing real time codes and in that environment there is what is called Message Passing from one process to another process or from one thread to another thread.

I just switched to Ubuntu and I would like to do the same thing in Ubuntu. I wrote a simple code just to try out the message passing. However there is an error when I compile it. Is there anyway I could solve it in Ubuntu?

I compile it by using 

```
cc -o try try.c -lpthread
```

The error that it return:

try.c:4:24: error: sys/iofunc.h: No such file or directory
try.c:5:26: error: sys/dispatch.h: No such file or directory
try.c: In function ‘main’:
try.c:21: error: ‘name_attach_t’ undeclared (first use in this function)
try.c:21: error: (Each undeclared identifier is reported only once
try.c:21: error: for each function it appears in.)
try.c:21: error: ‘identity_name’ undeclared (first use in this function)

My code is as follow:
```
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <sys/iofunc.h>
#include <sys/dispatch.h>

void *identity (void *s)
{
	int i;	
	int server_id = name_open ("identity",0);
	
	printf ("Input a number:\n");
	scanf ("%d",&i);
	MsgSend (server_id,&i,sizeof(int),NULL,0);
	return 0;
}

int main (void)
{
	int i,rcvid;
	name_attach_t *identity_name;
	pthread_t my_thread;

	identity_name=name_attach(NULL,"identity",0);
	
	pthread_create (&my_thread,NULL,identity,NULL);
	
	rcvid = MsgReceive (identity_name->chid,&i,sizeof(int),NULL);
	MsgReply (rcvid,1,NULL,0);
	printf ("The number you typed in before %d\n",i);
	return 0;
}
```

---

### Post by LaRoza on 2007-11-23
I spent a lot of time looking into this, are your sure iofunc.h and dispatch.h are for Linux? It seems to be QNX specific. You can use the POSIX standards for threading.

---

### Post by volanin on 2007-11-23
These functions are indeed QNX only.
They are implemented in QNX at a kernel level.

To communicate between threads in Linux, you can use normal global variables.
They are visible to every thread in the same process/program.
Just be sure to do proper mutex locking.

To communicate between different processes/programs, you have to use the
POSIX standard for passing messages. Unfortunately, there is nothing so
simple and concise as in QNX, so you will have to do some reading.

I suggest Beej's Guide to Unix Interprocess Communication:
[http://www.ecst.csuchico.edu/~beej/guide/ipc/](http://www.ecst.csuchico.edu/~beej/guide/ipc/)

Another good option that you have is passing messages through the userspace
message daemon DBUS. It's is available in every distribution, and is very efficient.
[http://dbus.freedesktop.org/doc/dbus-tutorial.html](http://dbus.freedesktop.org/doc/dbus-tutorial.html)

---

### Post by Game_Ender on 2008-05-24
As said above, you can't just copy and paste QNX sample code to Linux then do a little dance because you just saved thousands of dollars.  You really do get something for the money you pay.

If you want to switch a QNX application to Ubuntu you should use a kernel with the real time patches applied and write your own real time message queue.  Then you need to spend some time an assure yourself you implementation is as deterministic as your application requires.

EDIT: Wow, didn't realize how old this thread is.  Please ignore me.

---

### Post by Lau_of_DK on 2008-05-24
> **Game_Ender said:**
> As said above, you can't just copy and paste QNX sample code to Linux then do a little dance because you just saved thousands of dollars.  You really do get something for the money you pay.

If you want to switch a QNX application to Ubuntu you should use a kernel with the real time patches applied and write your own real time message queue.  Then you need to spend some time an assure yourself you implementation is as deterministic as your application requires.

EDIT: Wow, didn't realize how old this thread is.  Please ignore me.

Haha! 'bout the funniest thing on the Forum all day!

I knew there was something fishy about this thread, when LaRoza didn't just paste a link to faq/sticky :)

:lolflag:

---

### Post by CptPicard on 2008-05-24
Lulz, isn't it just so funny to pointlessly continue a thread that was necroed and where it was already asked to ignore it? :)

---

### Post by Lau_of_DK on 2008-05-25
> **CptPicard said:**
> Lulz, isn't it just so funny to pointlessly continue a thread that was necroed and where it was already asked to ignore it? :)

Absolutely, its for the common good :)  :popcorn:

---

