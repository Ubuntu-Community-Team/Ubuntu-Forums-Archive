---
title: "Communication between two C programs."
date: 2008-11-09
forum: Programming Talk
---

### Post by Big_Nose on 2008-11-09
Hi guys. As the title suggests, I'm trying to pass data from one C program to another, in real time. One of the programs is generating XYZ co-ordinates of an object in space, that change every second (or any specified update rate).

A second program needs to take this data and does some maths on it. Now I know I could easily do this in a single program, but I do need these to run as two separate programs, running in two separate terminal windows (for reasons that are a bit complicated to go into).

So far, all the methods I've Googled have either been communication between two processes (but from the same program), or they require one program to finish what it's doing and close, before the data is sent (not real time).

Please, has anyone got any ideas of how this can be done, I'm fairly new to C, so some example code that I could copypasta would be fantastic!

Thanks very much in advance!

---

### Post by Cracauer on 2008-11-09
"Real time"? What exactly do you mean by that? Do you want the data transparently shared? Use shared memory.

You can open two terminals in one program.

---

### Post by dribeas on 2008-11-09
> **Big_Nose said:**
> So far, all the methods I've Googled have either been communication between two processes (but from the same program), or they require one program to finish what it's doing and close, before the data is sent (not real time).


Usual solutions to your problem (I don't know how you did not come to them through google) are shared memory, pipes, sockets or some higher level communication system (CORBA, ICE, ...) I don't have samples, nor the time to work on them, but google for it and you'll find plenty of them.

---

### Post by gnusci on 2008-11-09
I did something like that long time ago with MICO:

[http://www.mico.org/](http://www.mico.org/)

---

### Post by tom66 on 2008-11-09
I don't know if this works, so...

 - Allocate required memory to store coordinates, and write the position of that memory (pointer) in a file.
 - With process #2, read file, create set pointer to data.
 - Use data.

---

### Post by pp. on 2008-11-09
You might want to try sending your data from/to [http://localhost](http://localhost)

---

### Post by dribeas on 2008-11-09
> **tom66 said:**
> I don't know if this works, so...

 - Allocate required memory to store coordinates, and write the position of that memory (pointer) in a file.
 - With process #2, read file, create set pointer to data.
 - Use data.

It won't work, address spaces for different processes are different. Even with shared memory, each process can see the shared memory in a different location. That without going into the whole issue that just having a pointer won't grant you access to that memory.

---

### Post by slavik on 2008-11-09
so many suggestions and so close, yet so far away ...

@dribeas, shared memory is seen the same by two processes. :)

read about SysV IPC.
shared memory (lock it with semaphores)
message queues
unix sockets
pipes (aka fifo)

---

### Post by Big_Nose on 2008-11-09
Hi guys, thanks for all your help! (and a really quick response! This was my first post)

I'll go with shared memory, I don't know why I hadn't researched that option, I think it is discouraged in some circles, but I'll give it a try, it looks like it should do the job for me.

I have been using some piping using popen in other parts of my program, but that's to run a 'wget' command from within the program, but like i said i'm pretty new to C, and all the sample code demonstrating piping between two processes just confuses me.

I'll give Shared memory a go, I see no reason why it shouldn't work.

Thanks again for all your help!

P.S. By 'real time' i mean both programs run constantly (until user terminates them) and are required to produce results with respect to time. Please correct me if i'm using the wrong terminology.

---

### Post by dribeas on 2008-11-10
> **slavik said:**
> @dribeas, shared memory is seen the same by two processes. :)

read about SysV IPC.
shared memory (lock it with semaphores)
message queues
unix sockets
pipes (aka fifo)

Just to make sure I have runned a couple of samples downloaded from the internet. After calling shmat in each of the processes, each process receives a different pointer value (convert the pointer into an int and print it with printf). 

Even if the memory pointed to is in the same physical location (hardware memory) the pointers are different, as memory address spaces are different for each process.

That is: you cannot send the address from one process to another and expect that it points to the same shared memory location, which is what the poster was suggesting.

---

### Post by cb951303 on 2008-11-10
I would use D-Bus

---

### Post by slavik on 2008-11-10
> **cb951303 said:**
> I would use D-Bus
I don't think D-Bus is that fast ...

---

### Post by slavik on 2008-11-10
> **dribeas said:**
> Just to make sure I have runned a couple of samples downloaded from the internet. After calling shmat in each of the processes, each process receives a different pointer value (convert the pointer into an int and print it with printf). 

Even if the memory pointed to is in the same physical location (hardware memory) the pointers are different, as memory address spaces are different for each process.

That is: you cannot send the address from one process to another and expect that it points to the same shared memory location, which is what the poster was suggesting.
int shmget(key_t key, size_t size, int shmflg);

Make sure the key is the same, then both programs will see the same shared memory segment. I would also suggest putting a value in and seeing if the other program gets the correct value when testing. Don't forget that there is something called Table Look aside Buffer. :)

---

### Post by dribeas on 2008-11-10
> **slavik said:**
> int shmget(key_t key, size_t size, int shmflg);

Make sure the key is the same, then both programs will see the same shared memory segment. I would also suggest putting a value in and seeing if the other program gets the correct value when testing. Don't forget that there is something called Table Look aside Buffer. :)

We are having a misunderstanding here. I will try to clear my point as much as possible. With shared memory, you can make two processes access the same memory, lets say that it is located at address 1000 in real memory (hardware). That is what shared memory is about.

There was a post saying that one process could write the pointer to a file/pipe and the other process could read and use it. That is wrong for two reasons: first is that if you don't explicitly request shared memory it won't be accessible by the other process.

And then there is the second issue that is keeping our own particular discussion. When you use shared memory, the OS gives you a pointer into that hardware memory area, but since each process has its own address space if you dump to screen/file/pipe the value of the pointer (not the pointed element, but the memory address itself) then the values will differ for each of the processes. While this can be counterintuitive at first (after all, both pointers do point to the same real memory), just run two simple test processes that requests to share memory and print the address of the memory (contents of the pointer) to screen and you will see that the value of the pointer is different.

This is mainly useless for the post, so I will not discuss it further. If you want I can send you test code (downloaded from the internet with slight modifications) to see the effect taking place.

---

### Post by dwhitney67 on 2008-11-10
I think the OP should consider using a queue of some sort; perhaps a Message Queue, or perhaps use a TCP socket (which is more efficient) where data messages can be queued.

Shared Memory will require the main application to define a fixed-sized structure.  That means the main application may need to block (when no additional space is available for the next data set) if the other application (the one processing the data) falls behind.  A variable-sized queue could remedy this, although there are chances where blocking may still occur.

---

### Post by bboozzoo on 2008-11-10
I always found SysV interface confusing, POSIX seems to be much cleaner:
1. shm_open (create shm, obtain file descriptor)
2. ftruncate (set size)
3. mmap
4. work, work
5. shm_unlink
for synchronization you can use:
1. sem_init(.., 1 /* shared */, 0);
2. sem_post
3. sem_wait
4. sem_destroy
taking everything together, is should be quite easy to make up a circular buffer

if you'd prefer message queues then POSIX comes with:
mq_open, mq_close, mq_send.... consult mq_overview(7)

---

### Post by Cracauer on 2008-11-10
Technically speaking, you can make pointers compatible.

Instead of SYSV shm you use mmap with MAP_SHARED. You just walk up virtual memory, supplying the first argument, in both programs, until you find one address that mmap allows you to use in both programs. Then pointers inside that area pointing to other addresses inside the area would work.

I think the original poster is confused in the first place, but that's besides the point :) If what is really needed is two terminals, open a second terminal.

---

### Post by puneeth@web on 2010-01-19
got an idea...
 
--------------------------------port 1.c-------------------------------------------------------
#include<stdio.h>
struct com
{
int (*port1)();
int (*port2)();
};
int val=0;
int portcomm()
{
 printf("port2");
 return val;
}
void READPORT(struct com *commadd)
{
FILE *f;
f=fopen("CONNECT.BIN","r");
if(f==NULL)
{
 printf("ERR..");
 exit(0);
}
fread(commadd,sizeof(struct com),1,f);
fclose(f);
}
void WRITEPORT(struct com *commadd)
{
FILE *f;
f=fopen("CONNECT.BIN","w");
if(f==NULL)
{
 printf("Can't Establish CONNECTION:");
 exit(0);
}
if(commadd->port1==NULL)
{
 printf("Din't Register port: ");
 exit(0);
}
fwrite(commadd,sizeof(struct com),1,f);
printf("%u\n",commadd->port1);
fclose(f);
}
void main()
{
 int p=0;
 struct com connection1;
 connection1.port1=portcomm;
 connection1.port2=NULL;
 clrscr();
 WRITEPORT(&connection1);
 //READPORT(&connection1);
 while(p!=-1)
 {
  scanf("%d",&p);
  val=p;
  if(connection1.port2!=NULL)
  {
   int (*temp)();
   temp=connection1.port2;
   printf("%d",(*temp)());
  }
 }
}
------------------------------------------------port 3--------------------------------------------
#include<stdio.h>
struct com
{
int (*port1)();
int (*port2)();
};
int val=0;
int portcomm()
{
 printf("port2");
 return val;
}
void READPORT(struct com *commadd)
{
FILE *f;
int i;
f=fopen("CONNECT.BIN","r");
if(f==NULL)
{
 printf("ERR..");
 exit(0);
}
i=fread(commadd,sizeof(struct com),1,f);
printf("%d\n",i);
fclose(f);
}
void CREATECONN(struct com *commadd)
{
FILE *f;
f=fopen("CONNECT.BIN","w");
if(f==NULL)
{
 printf("Can't Establish CONNECTION:");
 exit(0);
}
if(commadd->port2==NULL)
{
 printf("Din't Register port: ");
 exit(0);
}
fwrite(commadd,sizeof(struct com),1,f);
fclose(f);
}
void main()
{
 int p=0;
 struct com connection1;
 connection1.port2=portcomm;
 connection1.port1=NULL;
 //WRITEPORT(&connection1);
 clrscr();
 READPORT(&connection1);
 while(p!=-1)
 {
  scanf("%d",&p);
  val=p;
  if(connection1.port1!=NULL)
  {
   int (*temp)();
   temp=connection1.port1;
   printf("%d",(*temp)());
  }
 }
}
---------------------------------------------------------------------------------------------------
this does not work...??
so got any ideas....

---

### Post by redbrain on 2010-01-19
Well there are 2 or 3 main ways of doing this and really only 2 of them are useful.

1 -> dump contents into file's and have some kind of file mutex system with .pid files or something. But this is just a BAD idea makes a VERY messy program.

2 -> Networking this is an ok idea use UNIX sockets or simply tcp networking on localhost but its only useful if you want to be a distributed system.

3 -> the best way, message passing frameworks, things like D-bus or Dcop were designed for this but if your worried about speed you can use [http://en.wikipedia.org/wiki/Message_Passing_Interface](http://en.wikipedia.org/wiki/Message_Passing_Interface) MPI but this is made for distributed memory system processors like the Cell where every thread has its own memory/stack frame, but most of us are using shared memory systems on x86 so it doesn't really make sense to use MPI.

---

### Post by not_a_phd on 2010-01-19
I would use a UDP socket. Useful for when timeliness of the data is more important than guaranteed delivery. This provides the additional flexibility of permitting the two apps to run on two separate computers.

---

### Post by lisati on 2010-01-19
> **redbrain said:**
> Well there are 2 or 3 main ways of doing this and really only 2 of them are useful.

1 -> dump contents into file's and have some kind of file mutex system with .pid files or something. But this is just a BAD idea makes a VERY messy program.

2 -> Networking this is an ok idea use UNIX sockets or simply tcp networking on localhost but its only useful if you want to be a distributed system.

3 -> the best way, message passing frameworks, things like D-bus or Dcop were designed for this but if your worried about speed you can use [http://en.wikipedia.org/wiki/Message_Passing_Interface](http://en.wikipedia.org/wiki/Message_Passing_Interface) MPI but this is made for distributed memory system processors like the Cell where every thread has its own memory/stack frame, but most of us are using shared memory systems on x86 so it doesn't really make sense to use MPI.

I was about to suggest something along the lines of #1, but got beaten to it. 

Opinion: there are a whole bunch of nuggets here in this thread, it wouldn't surprise me if the final solution draws on several of them.

---

### Post by puneeth@web on 2010-01-27
thanks a lot i'll try networking....
 
but my motive is that program2 to should call a function say xyz() present in program1 ..!??

---

### Post by lisati on 2010-01-27
> **puneeth@web said:**
> thanks a lot i'll try networking....
 
but my motive is that program2 to should call a function say xyz() present in program1 ..!??

My first thought is to suggest searching for something something similar in operation to DLLs....

---

### Post by puneeth@web on 2010-01-27
That is exactly wat i was looking for ....
thanks.
 
but i'm just curious 
since Dll's are os dependent can i get something that is not dependent on OS
like the hardware location of funtion or something ....
 
basically what i want to do is similar to what signal handling does in unix...!
Unix calls the registered funtion when ever an event occured..!
i think its familiar

---

