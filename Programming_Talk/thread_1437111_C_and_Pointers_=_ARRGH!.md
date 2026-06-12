---
title: "C and Pointers = ARRGH!"
date: 2010-03-23
forum: Programming Talk
---

### Post by CraigWatson on 2010-03-23
I'm having a major headache with some code, and it's down to my (rather crap) understanding of pointers.

I have the following code fragment:

```

------- Header file -------
#define SOME_PORT 60666

------- main.c -------
create_socket_thread(SOME_PORT);

------- in sockets.c -------
/** Creates a thread for the socket connection **/
void create_socket_thread(int port){

	pthread_t thread;
	int *ptr = &port;
	printf("Will be listening on port %d\n",*ptr);
	
	pthread_create(&thread, NULL, create_socket, (void *) ptr);
}

/** Function adapted from Dave Price's "Network Programming From C" slides **/
void *create_socket(void *port_number){

    int port = *((int *) port_number);
    printf("Listening on port %d\n",port);
}

```

The rest of the code is unimportant and works, however all I want the function to do at the moment is output an integer value of the port number. Current output is:

```
Will be listening on port 60666
Listening on port 0
```

Is there anyone who can actually fix the code above and explain the principles behind where I'm going wrong? :)

---

### Post by MadCow108 on 2010-03-23
the argument port of create_socket_thread gets destroyed when the function ends.
This means when the thread starts, the pointer is very likely to be invalid.

you have to copy the value into the thread by saving the value in the pointer variable :
pthread_create(&thread, NULL, create_socket, (void *) **port**);
in the thread:
int port = (int)port_number; // an extra long cast may be required for portability

or make sure the value the pointer points to stays valid for the entire required lifetime (e.g. by letting the creater thread wait for the thread to end with pthread_join)

---

### Post by MindSz on 2010-03-23
My pointer programming is very rusty, but there's a couple of things you can try. First, shouldn't integers have a value between -32,767 and 32,767?

Also, instead of doing everything in one line like:

```
int port = *((int *) port_number);
```

you can try to do it step by step and check the values you are getting at each step (either with gdb or with print statements).

anyway, good luck!

EDIT: OR, you can try to do what MadCow said :)

---

### Post by n0dix on 2010-03-23
Try with:
```
int port = (int) port_number; 
```
instead 
```
int port = *((int *) port_number);
```

---

### Post by CraigWatson on 2010-03-23
> **MadCow108 said:**
> the argument port of create_socket_thread gets destroyed when the function ends.
This means when the thread starts, the pointer is very likely to be invalid.

you have to copy the value into the thread by saving the value in the pointer variable :
pthread_create(&thread, NULL, create_socket, (void *) **port**);
in the thread:
int port = (int)port_number; // an extra long cast may be required for portability

or make sure the value the pointer points to stays valid for the entire required lifetime (e.g. by letting the creater thread wait for the thread to end with pthread_join)

MadCow: that worked, thanks! Just a couple of minor niggles though, I'm trying to work out as many compilation warning as possible, and I get these for the void and int casts:

**cast to pointer from integer of different size**

---

### Post by MadCow108 on 2010-03-23
you probably have a 64 bit machine?
this means pointers are 8 byte whereas ints are 4bytes

so to cease the warning save the port in a type with the same size as the pointer.
intptr_t defined in inttypes.h is guaranteed to have the right size:

#include <inttypes.h>

intptr_t port = 1024;
...
intptr_t port = (intptr_t)port_number

to print this number portably you will need the macros also defined in inttypes.h
[http://www.opengroup.org/onlinepubs/000095399/basedefs/inttypes.h.html](http://www.opengroup.org/onlinepubs/000095399/basedefs/inttypes.h.html)

if you don't care just use %ld

---

### Post by CraigWatson on 2010-03-23
> **MadCow108 said:**
> you probably have a 64 bit machine?
this means pointers are 8 byte whereas ints are 4bytes

so to cease the warning save the port in a type with the same size as the pointer.
intptr_t defined in inttypes.h is guaranteed to have the right size:

#include <inttypes.h>

intptr_t port = 1024;
...
intptr_t port = (intptr_t)port_number


Thanks :) After a bit of Googling I can see that I'm probably going to end up creating more problems by using intptr_t instead of int, so I'll probably end up chasing my own tail so-to-speak for the sake of a couple of compiler warnings.

Are there any adverse effects of using int vs intptr_t? Thanks for the help :)

---

### Post by MadCow108 on 2010-03-23
I think on x86 machines your fine.
But on other architectures there may be problems.

What problems do you see in using intptr_t?
the only drawback I see is the increased typing needs for printing.
But for debugging you can just stick to %ld to save some letters.

An addition to the second possibility mentioned above to avoid all this:
you could dynamically allocate the port number in the thread creator and let the thread take care of the deallocation.

---

### Post by dwhitney67 on 2010-03-24
Port numbers range from 0 to 65,535 (2^16 - 1), so technically you should consider declaring the port number to be an unsigned short.

As for declaring your port number using a macro, this should be avoided for two reasons:  1) no type is associated with a macro declaration, and 2) the macro's value is not stored within the program space of the application -- thus it is not addressable.

Consider the following:
```

#include <pthread.h>
#include <stdio.h>

void* create_socket(void* arg)
{
   unsigned short port = *(unsigned short*)(arg);

   printf("thread is using port = %u\n", port);

   return 0;
}

pthread_t create_socket_thread(const unsigned short* port)
{
   pthread_t tid;

   pthread_create(&tid, 0, create_socket, (void*) port);

   return tid;
}

int main(void)
{
   const unsigned short port = 25000;

   pthread_t tid = create_socket_thread(&port);

   pthread_join(tid, 0);

   return 0;
}

```

P.S.  Feel free to replace the 'unsigned short' with 'int'; the main point above is to avoid using a macro.

---

### Post by MadCow108 on 2010-03-24
which macro are you talking about?
intptr_t is a typedef

the macros I mentioned are just needed for portable use in the format part of printf/scanf like statements

edit: this is incorrect:
using short in dwhitney's way will still trigger the differing size warning on most systems
editend

here pseudo code of what I think is the best, most portable and warning free way (next to letting the creator wait for the thread to end):
```

create_thread()
{
  // use whatever type you wish
  unsigned short * port_ptr = (unsigned short *)malloc(sizeof(unsigned short));
  *port_ptr = 1024;
  pthread_create(..., (void*)port_ptr);
}

thread(..., void *arg)
{
  unsigned short port = *(unsigned short*)arg;
  free(arg);
}

```

---

### Post by dwhitney67 on 2010-03-24
> **MadCow108 said:**
> which macro are you talking about?

From the OP's opening post:
```

------- Header file -------
#define SOME_PORT 60666

```

> **MadCow108 said:**
> 
using short in dwhitney's way will still trigger the differing size warning on most systems

Which systems?  I tested the code on Ubuntu 9.10 (32-bit), Mac OS-X (32 bit), and RHEL 5.8 (64-bit).  No warnings, no errors!

---

### Post by MadCow108 on 2010-03-24
I'm sorry I misinterpreted your code wrong. It is indeed warning free.

---

### Post by johnl on 2010-03-24
Just to chime in, you can avoid the compiler warning and have your code be 'correct' by using a somewhat ugly double cast:

```

/* port is of type int */

pthread_create(&tid, 0, create_socket, (void*)(intptr_t)port);


```


Casting port to intptr_t will widen it to 64-bits (on a machine with 64-bit pointers), and then casting to void* from inptr_t is OK.

---

