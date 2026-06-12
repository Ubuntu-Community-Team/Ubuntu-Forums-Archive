---
title: "Memory leaks"
date: 2010-09-27
forum: Programming Talk
---

### Post by hosseinyounesi on 2010-09-27
Hi everyone,

I'm using pthreads for a multithreaded program. here is a sample code:

```

while(1):
{
Accepter = accept( ListenSocket, NULL, NULL );
cout << "Accepted" << endl;
pthread_t t;
int err=0;
err=pthread_create(&t,NULL,ProcessThread,(void*)Accepter);
}

void * ProcessThread(void * arg)
{
int Accepter = (int)arg;
/*WORK*/
shutdown(Accepter,SHUT_RDWR);
close(Accepter);
}

```

Questions:

1) There is a problem in this code. Memory used by this program is ALWAYS INCREASING by accepting new connections!!! It seems that after thread function termination the pthread doesn't release the memory!?! Why? Should I use detach, exit or cleanup? detach first and then exit? where should I call them ?(end of thread function). Any other issues?

2) Is there any problem with my "Accepter" variable?!!

3) I have many connections but processing them is mostly less than a sec. Can I thread pool? If yes, how can I do that with pthread?

Thanks a lot b4

---

### Post by MadCow108 on 2010-09-27
1. you have to detach the thread or join them again at some point.
Otherwise you will leak memory.
> 
pthread_attr_t attr;
pthread_attr_init(&attr);
pthread_attr_setdetachstate(&attr, PTHREAD_CREATE_DETACHED);


2. The error checking on the Accepter variable is missing.
you should use an type which has the same with as an pointer.
In C99 this would be intptr_t from <inttypes.h>
pre C99 long mostly does it.

3. yes you can thread pool, and it may be faster, but as you will have to code it yourself for use a library.
pthread does not have this built in.

---

### Post by hosseinyounesi on 2010-09-27
Thanks MadCow108.

Another question:
What's wrong with following command:
```

pthread_mutex_t mutex[MAX_THREADS];
for(int i=0;i<MAX_THREADS;i++)
{
      mutex[i]=PTHREAD_MUTEX_INITIALIZER;
}

```

after compile the following warning is shown:
> 
extended initializer lists only available with -std=c++0x or -std=gnu++0x 


---

### Post by MadCow108 on 2010-09-27
g++ is to dumb to figure out this is all compile time defined.
so it "initializes" the array in the first line and fails when you want to initialize it again in the loop.

use pthread_mutex_init instead or (less recommended) initialize it by hand in the first line (ar[] = {INIT, INIT, INIT}).

---

### Post by hosseinyounesi on 2010-09-27
Thanks again,

1) But my main problem (memory leakage) is not solved :(
I wrote detach and exit at end of each thread, but memory is increasing although slower! What's wrong? It appears that although I'm detaching thread or freeing or deleting my memory, OS is not freeing that! I wrote a thread pool too with 100 threads, so threads never die. I assumed that If i use thread pool, required memory will be allocated in program start and no memory increase will be done. But still the same!!!!!!!!!

(Better to mention that I'm using XMLParser too.)

2) It seems that I should use fork instead of pthread?! What are issues? forking overhead is more than pthread? how? I have more than 500 clients that each will connect every 30 secs.


Please help, thanks

---

### Post by dwhitney67 on 2010-09-27
> **hosseinyounesi said:**
> Thanks again,

1) But my main problem (memory leakage) is not solved :(
I wrote detach and exit at end of each thread, but memory is increasing although slower! What's wrong? It appears that although I'm detaching thread or freeing or deleting my memory, OS is not freeing that! I wrote a thread pool too with 100 threads, so threads never die. I assumed that If i use thread pool, required memory will be allocated in program start and no memory increase will be done. But still the same!!!!!!!!!

(Better to mention that I'm using XMLParser too.)

2) It seems that I should use fork instead of pthread?! What are issues? forking overhead is more than pthread? how? I have more than 500 clients that each will connect every 30 secs.


Please help, thanks

Are you allocating anything in this section of the code:
```

...
/*WORK*/
...

```

Why would your clients connect so often?  Why not just stay connected?

If you are using a thread-pool, then it would be interesting to see how you have implemented it.  I noticed from the code in your opening post that you are using C++.

---

### Post by hosseinyounesi on 2010-09-27
> 
Are you allocating anything in this section of the code:
```

...
/*WORK*/
...

```

Yes i'm allocating but be sure that i free or delete it too!

> Why would your clients connect so often?  Why not just stay connected?

Stay connected for at least 30 secs?!!!

> 
If you are using a thread-pool, then it would be interesting to see how you have implemented it.  I noticed from the code in your opening post that you are using C++.


Here it is:
```

mutex = (pthread_mutex_t*) malloc( MAX_THREADS*sizeof(pthread_mutex_t) );
thrd = (pthread_t*) malloc( MAX_THREADS*sizeof(pthread_t) );
ti = (ThreadInfo*) malloc( MAX_THREADS*sizeof(ThreadInfo) );
//initialize
for(int i=0;i<MAX_THREADS;i++)
{
	pthread_mutex_init(&mutex[i],NULL);
}
//block all threads
for(int i=0;i<MAX_THREADS;i++)
{
        pthread_mutex_lock(&mutex[i]);
}
//pool creation
for(int i=0;i<MAX_THREADS;i++)
{
	pthread_create(&thrd[i],NULL,ProcessThread,(void*)i);
	//all threads are available
	availableThreads.push_back(i);
}

while(true)
{
	Accepter = accept( ListenSocket, NULL, NULL );
	cout << "Accepted" << endl;
	if( Accepter==-1 ) {
		sprintf(logstr,"%d",errno);
		LOG_ERROR(logstr,"couldn't accept");
		continue;
	}
	if(availableThreads.size()!=0)
	{
		pthread_mutex_lock(&data_mutex);
		int index=availableThreads.front();
		availableThreads.pop_front();
		ti[index].Accepter=Accepter;
		pthread_mutex_unlock(&data_mutex);
		pthread_mutex_unlock(&mutex[index]);
	}
}

void * ProcessThread(void * arg)
{
        pthread_mutex_lock(&mutex[i]);

	pthread_mutex_lock(&data_mutex);
	Accepter=ti[i].Accepter;
	availableThreads.remove(i);
	pthread_mutex_unlock(&data_mutex);

        SEND & RECV
        PARSING PACKET
        FREE MEMORIES

        pthread_detach(pthread_self())

        pthread_mutex_lock(&data_mutex);
	availableThreads.push_back(i);
	pthread_mutex_unlock(&data_mutex);

}

```

Memory size just increases slowly?!!! and after a while I got "Virtual memory exhausted."!
detach will release the memory? should i use setstack? I'm really confused with pthread and linux :(

Waiting for your answers, thanks a lot

---

### Post by percyhahn on 2010-09-27
i dont mean to sound completely stupid, but how do you get memory leakage? what sort of memory leakage, like RAM? or storage memory?
     lehmans terms will be fine :P as i dont really know anything about programming, this title just took my interest :)

---

### Post by dwhitney67 on 2010-09-27
> **hosseinyounesi said:**
> 
Memory size just increases slowly?!!! detach will release the memory? should i use setstack? I'm really confused with pthread and linux :(

Waiting for your answers, thanks a lot

My experience with POSIX threads is also limited, but I do have some ideas.

First of all, do not destroy the thread(s) after they have been invoked.  Stall them, but don't destroy them... for this is costly in terms of CPU cycles.

All of your threads do the same thing using one common data parameter... a socket ID.

I know this may seem like a step into left field, but take a moment to think about what you are attempting to accomplish.  From what I see, you have a parent thread with many child-threads.  It would be helpful if these child-threads were made aware of their parent, and the (yet to be defined) functions this parent offers.

Your parent-thread should provide the means for your child-threads to say "pick me! pick me!" when the child is done processing a client.  Thus the child-thread needs the mean to notify the parent that it is done processing a client.

Consider this (and believe me, I've never done exactly like this before, but something similar):
```

class Thread
{
public:
   void start()
   {
      pthread_create(&tid, 0, helper, this);
   }

   inline pthread_t getTID() const { return tid; }

protected:
   Thread();

   virtual void run() = 0;

private:
   static void* helper(void* arg)
   {
      Thread* t = reinterpret_cast<Thread*>(arg);

      t->run();

      return 0;
   }

   pthread_t tid;
};


class ParentThread : public Thread
{
public:
   ParentThread(int numChildThreads, int portNumber);

   void childIsDone(int childID);

private:
   void run();

   std::vector<ChildThreads> childThreadPool;
   std::queue<int>           availableChildThreadIDs;
   int                       listenSocket;
};

class ChildThread : public Thread
{
public:
   ChildThread(ParentThread& parent, int childID, pthread_mutex_t& mutex);

   void handleClient(int clientSocket);

private:
   void run();

   ParentThread&    parent;
   int              childID;
   pthread_mutex_t& mutex;
   int              clientSocket;
   bool             remainIdle;
};

```
Here, the Parent Thread creates N child threads, which by default should be sitting idle, which means that even though they are running, they are not processing anything.

When a child is needed, the Parent Thread obtains an available ID from the queue (something similar to what you are already doing).  If successful in getting a child, the parent informs the child of the client socket identifier, and from that point the child does something constructive.

When the child is done, it notifies it's parent, via the parent's childIsDone() method that it is done... and in essence, wants to be re-inserted into the queue.  It then goes back into an idle mode.

With this design, I'm not sure if the Child Thread really needs a mutex, unless it is sharing access to data objects shared by other Child Threads or the Parent.  Access to the Parent's queue should definitely be mutex protected, but you require only one mutex for this, not N mutexes.

---

### Post by hosseinyounesi on 2010-09-27
Thanks you dwhitney67,

But I don't think that your way will help me about memory increasing problem. Have you used fork before? Is that a good idea to use fork instead of thread?

Thanks

---

### Post by worseisworser on 2010-09-27
It's kinda hard to tell what's leaking because you do not show the entire code.

Perhaps you can deal with this yourself by using Valgrind?

---

### Post by dwhitney67 on 2010-09-27
Forking a process is expensive, considering that it is a full-blown process versus that of a light-weight process (ie. thread).

I will get back to you with a full/working solution to what I was proposing earlier.  It should be scalable to using any number of threads.

P.S.  When I think about it more, the solution I proposed earlier probably was similar to a design I developed which would allow one or more clients (literally, users) to connect to, and interact with, a shell running under VxWorks.  The VxWorks OS was being used to support the run-time environment for processes that were used to manage a satellite.  So needless to say, the client and the server were far apart!

---

### Post by dumbsnake on 2010-09-27
Using fork is probably not any more expensive, in fact, it may be less expensive, however, you will lose the ability to share memory (and a bunch of other stuff too). You also can NOT mix fork() with the creation of new threads without doing some very complicated locking and other stuff.

As far as your memory leak, you're running Linux, so take advantage of all the awesome that is provided. In particular, use valgrind. There is a package in Ubuntu for it, so just install that. Then, from the command line, run your program as follows:

```

$ valgrind --leak-check=yes ./your_program

```

This will print out information about where the memory is being allocated. You may have some other problems that it detects as well, but heck, that is why valgrind is awesome!

Also, you might want to google a bit more if you need additional info on valgrind. One last thing, make sure you are compiling your program with symbolic debugging information. If you are using gcc, you'll want to add the -g option. Good luck!

---

### Post by hosseinyounesi on 2010-09-28
Thanks all of you,

1) I decided to test my program with fork too. here it is:

```

void SigCatcher(int n)
{
	//Avoiding Zombie
	wait3(NULL,WNOHANG,NULL);
}

while(true)
{
	Accepter = accept( ListenSocket, NULL, NULL );
	cout << "Accepted" << endl;
	if( Accepter==-1 ) {
		sprintf(logstr,"%d",errno);
		LOG_ERROR(logstr,"couldn't accept");
		continue;
	}
	pid_t pID = fork();
	if (pID == 0)// child
	{
		ProcessFrok((void*)Accepter);
		exit(0);
	}
	else if (pID < 0)// failed to fork
	{
		cerr << "Failed to fork" << endl;
		LOG_ERROR("FATAL","Failed to fork.");
	}
}

void * ProcessFrok(void * arg)
{
        SEND & RECV
        PARSING PACKET
        FREE MEMORIES
	SHUTDOWN & CLOSE ACCEPTED SOCKET
}

```

I executed my program, it's working now for 3 hours. I'll report any possible problem. But is there any limitation for number of forking? For example parent can just 2000 childes?!

2) You are not talking about pthreads? It seems that multithreading in linux is not like windows?! I write the same program in linux with windows threads and it's working fine without any leakage! So what's wrong with pthreads or linux?

3) I'm using Valgrind and result will be reported too.

Thanks b4

---

### Post by hosseinyounesi on 2010-09-28
Hi again,

Forking example after a while is just printing "Accepted" again and again! But no child process is created and nothing is being logged!
Now I'm really confused :(

I have to mention that i used this for listening:

```
listen(ListenSocket, SOMAXCONN)
```

How about using libHoard? Anyone used it before?

---

### Post by worseisworser on 2010-09-28
I can help you with pthread, but it is impossible without some code...

---

### Post by dwhitney67 on 2010-09-28
> **dwhitney67 said:**
> 
I will get back to you with a full/working solution to what I was proposing earlier.  It should be scalable to using any number of threads.


I've attached a tar-ball with the working framework for implementing a thread-pool.  It is very basic, and it does not include any of the networking stuff that hosseinyounesi was working on.  The addition of the networking stuff has been left as an exercise.

hosseinyounesi, feel free to play with this code, and add the necessary hooks to have the child and parent thread terminate gracefully; of just rely on ctrl-c as I did.

Also test using valgrind; these are the results I got:
```

...
==9199== LEAK SUMMARY:
==9199==    definitely lost: 0 bytes in 0 blocks
==9199==    indirectly lost: 0 bytes in 0 blocks
==9199==      possibly lost: 864 bytes in 6 blocks
==9199==    still reachable: 696 bytes in 8 blocks
==9199==         suppressed: 0 bytes in 0 blocks
...

```

---

### Post by hosseinyounesi on 2010-09-28
I sent the code in message number 7. Please let me know what exactly should i send.

---

### Post by worseisworser on 2010-09-28
Something that actually compiles and runs on a computer and showing/illustrating the problem would be helpful; there's a million different things not shown here that *might* leak.

[http://www.catb.org/esr/faqs/smart-questions.html#code](http://www.catb.org/esr/faqs/smart-questions.html#code)
> 
The most effective way to be precise about a code problem is to provide a minimal bug-demonstrating test case. What's a minimal test case? It's an illustration of the problem; just enough code to exhibit the undesirable behavior and no more. How do you make a minimal test case? If you know what line or section of code is producing the problematic behavior, make a copy of it and add just enough supporting code to produce a complete example (i.e. enough that the source is acceptable to the compiler/interpreter/whatever application processes it). If you can't narrow it down to a particular section, make a copy of the source and start removing chunks that don't affect the problematic behavior. The smaller your minimal test case is, the better (see the section called &#8220;Volume is not precision&#8221;).

Generating a really small minimal test case will not always be possible, but trying to is good discipline. It may help you learn what you need to solve the problem on your own &#8212; and even when it doesn't, hackers like to see that you have tried. It will make them more cooperative.


People expect the same when posting bug-reports too by the way.

---

### Post by hosseinyounesi on 2010-09-28
Here is the code:

main:
```

mutex = (pthread_mutex_t*) malloc( MAX_THREADS*sizeof(pthread_mutex_t) );
thrd = (pthread_t*) malloc( MAX_THREADS*sizeof(pthread_t) );
/*ThreadInfo is the ret value of accept that is set as a global array for threads*/
ti = (ThreadInfo*) malloc( MAX_THREADS*sizeof(ThreadInfo) );
//initialize
for(int i=0;i<MAX_THREADS;i++)
{
	pthread_mutex_init(&mutex[i],NULL);
}
//block all threads
for(int i=0;i<MAX_THREADS;i++)
{
        pthread_mutex_lock(&mutex[i]);
}
//pool creation
for(int i=0;i<MAX_THREADS;i++)
{
	pthread_create(&thrd[i],NULL,ProcessThread,(void*)i);
	//all threads are available
	availableThreads.push_back(i);
}

while(true)
{
	Accepter = accept( ListenSocket, NULL, NULL );
	cout << "Accepted" << endl;
	if( Accepter==-1 ) {
		sprintf(logstr,"%d",errno);
		LOG_ERROR(logstr,"couldn't accept");
		continue;
	}
	if(availableThreads.size()!=0)
	{
		pthread_mutex_lock(&data_mutex);

		int index=availableThreads.front();
		availableThreads.pop_front();
		ti[index].Accepter=Accepter;

		pthread_mutex_unlock(&data_mutex);

		pthread_mutex_unlock(&mutex[index]);
	}
}

```

thread function:
```

void * ProcessThread(void * arg)
{

while(true)
{
pthread_mutex_lock(&mutex[i]);

pthread_mutex_lock(&data_mutex);
Accepter=ti[i].Accepter;
availableThreads.remove(i);
pthread_mutex_unlock(&data_mutex);

char* packet=NULL;
char* Resp=NULL;
char* respons=NULL;
char **test=NULL;
char logstr[100];
XMLNode Response,xmlpacket;
unsigned long size=0;
int i=(int)arg;
int Accepter=0;
char tmp;
struct timeval tv;

{
	tv.tv_sec = TIMEOUT;
	tv.tv_usec = 0;
	if( setsockopt(Accepter,SOL_SOCKET,SO_RCVTIMEO,(char*)&tv,sizeof(tv))==-1 )
	{
		sprintf(logstr,"%d",errno);
		LOG_ERROR(logstr,"Error in socket settings");
		goto Thread_Cleanup;
	}
}

size=0;
if(recv(Accepter,(char*)&size,sizeof(size),0)==-1) {//recieves the incoming packet's size!
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"Error in recv1");
	goto Thread_Cleanup;
}

if(send(Accepter,(char*)&tmp,1,0)==-1) {//sends ack
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"Error in send1");
	goto Thread_Cleanup;
}

packet=new char[size];
if(recv(Accepter,packet,size,0)==-1) {//recieves the packet
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"Error in recv2");
	goto Thread_Cleanup;
}
packet[size]=0;

XMLResults Xres;
if(strlen(packet)!=0)//packet is recieved as a string, so it should be parsed to xml format
	xmlpacket=XMLNode::parseString(packet,NULL,&Xres);


if(Xres.error == eXMLErrorNone)
	ProcessPacket(xmlpacket,Response);
else
{
	LOG_ERROR("XML_ERROR:",XMLNode::getError(Xres.error));
	goto Thread_Cleanup;
}

Resp = Response.createXMLString(0);
size = strlen(Resp)+1;
respons = new char[size];
strcpy(respons,Resp);

size=strlen(respons)+1;
if(send(Accepter,(char*)&size,sizeof(size),0)==-1) {//sends the size of response
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"Error in send2");
	goto Thread_Cleanup;
}

if(recv(Accepter,(char*)&tmp,1,0)==-1) {//recieves ack
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"Error in recv3");
	goto Thread_Cleanup;
}

if(send(Accepter,respons,size,0)==-1) {//sends the response
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"Error in send2");
	goto Thread_Cleanup;
}

Thread_Cleanup:
if(Resp)
	free(Resp);
if(packet)
	delete[] packet;
if(respons)
	delete[] respons;

usleep(500*1000);

if( shutdown(Accepter,SHUT_RDWR)==-1 ) {
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"couldn't shutdown socket");
}
if( close(Accepter)==-1) {
	sprintf(logstr,"%d",errno);
	LOG_ERROR(logstr,"couldn't close socket");
}


pthread_detach(pthread_self())

pthread_mutex_lock(&data_mutex);
availableThreads.push_back(i);
pthread_mutex_unlock(&data_mutex);

}
}

```

So this is my implementation of thread pool and socket programming. I'm using [[COLOR="Red"]libhoard[/COLOR]]("http://www.hoard.org/") and [[COLOR="Red"]XMLParser[/COLOR]]("http://www.applied-mathematics.net/tools/xmlParser.html")

---

### Post by dwhitney67 on 2010-09-28
hosseinyounesi -- Do you think you could possibly design your application in terms of objects?  In other words, can you please put together an OO design, where you separate object data from object actions.

You are allocating way too much more than you need.

Also, think carefully about the following... what is the value of 'i' at this point in the code?
```

void * ProcessThread(void * arg)
{

while(true)
{
**pthread_mutex_lock(&mutex[i]);**

pthread_mutex_lock(&data_mutex);
**Accepter=ti[i].Accepter;**
**availableThreads.remove(i);**
pthread_mutex_unlock(&data_mutex);

char* packet=NULL;
char* Resp=NULL;
char* respons=NULL;
char **test=NULL;
char logstr[100];
XMLNode Response,xmlpacket;
unsigned long size=0;
**int i=(int)arg;**
...

```

---

### Post by hosseinyounesi on 2010-09-29
Hi,

I just copied the code, int i=(int)arg is in beginning of function. You thick that OO can help me about memory? Or just readability?

---

### Post by dwhitney67 on 2010-09-29
> **hosseinyounesi said:**
> Hi,

I just copied the code, int i=(int)arg is in beginning of function. You thick that OO can help me about memory? Or just readability?

Readability is not only good for those who peer review your code, but ultimately it is good for the one developing the code.

You could define a Thread Object that encapsulates many of the entities it requires, without having to allocate them, or should I say declare them, elsewhere.  Keep your code simple, and it will be easier to manage.

For grins and also for educational purposes, I have put together a TCP Server application that handles multiple client connections.  The server maintains a pool of client handlers, that is uses to handle each client that connects.  If all client handlers are in use, and another client connects, well then it is not serviced.

Please take a look at the code, which I have attached.  Note that the server depends on an external Socket Library, which I have also attached.

Let me know if you have any questions, or suggestions on how to improve the code.

---

### Post by hosseinyounesi on 2010-10-01
Hi again,

I'm testing my code for large traffics, now after 3 days memory increasing is stopped (just increasing or decreasing 0.1 MB sometimes). 
Thanks for helps. But there is another problem! I'm using mysqlpp library, it works fine, but when there are too many connections it fails and this error appears:
> 
Access denied for user 'root'@'localhost' (using password: NO)


This is my plan for each client connection: connect to mysql (with mysqlpp), execute some queries and close the mysql connection. What's wrong?
Should I use persistent connection? open a connection and use it for all client connections and never close it?

Thanks b4

---

### Post by dwhitney67 on 2010-10-01
Read here about MySQL and the number of connections supported:
[http://dev.mysql.com/doc/refman/5.1/en/too-many-connections.html](http://dev.mysql.com/doc/refman/5.1/en/too-many-connections.html)

If you want to tweak the number of connections allowed, then I believe the appropriate file is /etc/mysql/my.cnf.  Look for the 'max_connections' variable, which is probably commented out.

---

### Post by hosseinyounesi on 2010-10-01
I'm not sure that it's because of MAX_CONNECTION. I increased max_connection and thread_concurrency. Nothing improved :(
Any other parameter?

Thanks

---

### Post by dwhitney67 on 2010-10-01
Sorry for asking the obvious, but did you restart the MySQL server after making the configuration updates?

---

### Post by hosseinyounesi on 2010-10-01
Yes i did :)
I'll ask my question in mysql++ forum and I'll report the result here.

Thanks again for your helps

---

### Post by hosseinyounesi on 2010-10-03
"Segmentation fault" ! This is the new exception from m program. After running for more than 5 days, the above error appeared. What's wrong? Nothing new happened in past days! How can I determine the "Segmentation fault" reason?

Thanks b4

---

### Post by dwhitney67 on 2010-10-03
Run you application with gdb (or ddd) and present it the core file.  For example:
```

gdb theapp corefile

```
The other alternative is to run it again using valgrind or gdb.

---

### Post by hosseinyounesi on 2010-10-03
Thanks, I will try it. Can gdb determine the stack over flow problems too?
As I have too many threads and socket connections, is there any possibility that the "segmentation fault" exception is because of threads stack size? Any limitation about that?

Thanks b4

---

### Post by hosseinyounesi on 2010-10-03
Hi again,

This is gdb output:

> 
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb56bab70 (LWP 32363)]
HL:: DLList::get (sz=41) at heaplayers/util/dllist.h:68
68	heaplayers/util/dllist.h: No such file or directory.
	in heaplayers/util/dllist.h


I'm using libhoard for better memory management. Is this hoard's problem or ...? This is really confusing :(
Any idea?

---

### Post by hosseinyounesi on 2010-10-03
I removed libhoard from the attached libraries, and now this is the gdb output:

> 
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x34b591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8 )[0x34cde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x34fecd]
/usr/lib/libmysqlclient.so.16(my_no_flags_free+0x21)[0x47d621]
/usr/lib/libmysqlclient.so.16(my_fclose+0x84)[0x481d24]
/usr/lib/libmysqlclient.so.16(+0x49b3f)[0x483b3f]
/usr/lib/libmysqlclient.so.16(+0x49d77)[0x483d77]
/usr/lib/libmysqlclient.so.16(my_search_option_files+0x28a)[0x48409a]
/usr/lib/libmysqlclient.so.16(my_load_defaults+0x137)[0x484317]
/usr/lib/libmysqlclient.so.16(mysql_read_default_options+0x62)[0x4a9782]
/usr/lib/libmysqlclient.so.16(mysql_real_connect+0xb6)[0x4ab0d6]
/usr/lib/libmysqlpp.so.3(_ZN7mysqlpp8DBDriver7connectEPKcS2_jS2_S2_S2_+0x10e)[0x179e4e]
/usr/lib/libmysqlpp.so.3(_ZN7mysqlpp10Connection7connectEPKcS2_S2_S2_j+0xbe)[0x1736be]
/root/workspace/AMSERVER/Debug/AMSERVER[0x806cc97]
/root/workspace/AMSERVER/Debug/AMSERVER[0x80623f9]
/root/workspace/AMSERVER/Debug/AMSERVER[0x8052621]
/root/workspace/AMSERVER/Debug/AMSERVER[0x80538bc]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0x13396e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0x3ada4e]
======= Memory map: ========
00110000-0012b000 r-xp 00000000 08:02 532393     /lib/ld-2.11.1.so
0012b000-0012c000 r--p 0001a000 08:02 532393     /lib/ld-2.11.1.so
0012c000-0012d000 rw-p 0001b000 08:02 532393     /lib/ld-2.11.1.so
0012d000-0012e000 r-xp 00000000 00:00 0          [vdso]
0012e000-00143000 r-xp 00000000 08:02 523421     /lib/tls/i686/cmov/libpthread-2.11.1.so
00143000-00144000 r--p 00014000 08:02 523421     /lib/tls/i686/cmov/libpthread-2.11.1.so
00144000-00145000 rw-p 00015000 08:02 523421     /lib/tls/i686/cmov/libpthread-2.11.1.so
00145000-00147000 rw-p 00000000 00:00 0 
00147000-0015f000 r-xp 00000000 08:02 272208     /usr/lib/librudeconfig.so.3.2.1
0015f000-00160000 rw-p 00018000 08:02 272208     /usr/lib/librudeconfig.so.3.2.1
00160000-001a2000 r-xp 00000000 08:02 271451     /usr/lib/libmysqlpp.so.3.0.9
001a2000-001a3000 ---p 00042000 08:02 271451     /usr/lib/libmysqlpp.so.3.0.9
001a3000-001a4000 r--p 00042000 08:02 271451     /usr/lib/libmysqlpp.so.3.0.9
001a4000-001a5000 rw-p 00043000 08:02 271451     /usr/lib/libmysqlpp.so.3.0.9
001a5000-0028e000 r-xp 00000000 08:02 265434     /usr/lib/libstdc++.so.6.0.13
0028e000-0028f000 ---p 000e9000 08:02 265434     /usr/lib/libstdc++.so.6.0.13
0028f000-00293000 r--p 000e9000 08:02 265434     /usr/lib/libstdc++.so.6.0.13
00293000-00294000 rw-p 000ed000 08:02 265434     /usr/lib/libstdc++.so.6.0.13
00294000-0029b000 rw-p 00000000 00:00 0 
0029b000-002bf000 r-xp 00000000 08:02 523362     /lib/tls/i686/cmov/libm-2.11.1.so
002bf000-002c0000 r--p 00023000 08:02 523362     /lib/tls/i686/cmov/libm-2.11.1.so
002c0000-002c1000 rw-p 00024000 08:02 523362     /lib/tls/i686/cmov/libm-2.11.1.so
002c1000-002de000 r-xp 00000000 08:02 523347     /lib/libgcc_s.so.1
002de000-002df000 r--p 0001c000 08:02 523347     /lib/libgcc_s.so.1
002df000-002e0000 rw-p 0001d000 08:02 523347     /lib/libgcc_s.so.1
002e0000-00433000 r-xp 00000000 08:02 523313     /lib/tls/i686/cmov/libc-2.11.1.so
00433000-00434000 ---p 00153000 08:02 523313     /lib/tls/i686/cmov/libc-2.11.1.so
00434000-00436000 r--p 00153000 08:02 523313     /lib/tls/i686/cmov/libc-2.11.1.so
00436000-00437000 rw-p 00155000 08:02 523313     /lib/tls/i686/cmov/libc-2.11.1.so
00437000-0043a000 rw-p 00000000 00:00 0 
0043a000-005e4000 r-xp 00000000 08:02 267499     /usr/lib/libmysqlclient.so.16.0.0
005e4000-005e5000 ---p 001aa000 08:02 267499     /usr/lib/libmysqlclient.so.16.0.0
005e5000-005e8000 r--p 001aa000 08:02 267499     /usr/lib/libmysqlclient.so.16.0.0
005e8000-0062d000 rw-p 001ad000 08:02 267499     /usr/lib/libmysqlclient.so.16.0.0
0062d000-0062e000 rw-p 00000000 00:00 0 
0062e000-00637000 r-xp 00000000 08:02 523321     /lib/tls/i686/cmov/libcrypt-2.11.1.so
00637000-00638000 r--p 00008000 08:02 523321     /lib/tls/i686/cmov/libcrypt-2.11.1.so
00638000-00639000 rw-p 00009000 08:02 523321     /lib/tls/i686/cmov/libcrypt-2.11.1.so
00639000-00660000 rw-p 00000000 00:00 0 
00660000-00673000 r-xp 00000000 08:02 523373     /lib/tls/i686/cmov/libnsl-2.11.1.so
00673000-00674000 r--p 00012000 08:02 523373     /lib/tls/i686/cmov/libnsl-2.11.1.so
00674000-00675000 rw-p 00013000 08:02 523373     /lib/tls/i686/cmov/libnsl-2.11.1.so
00675000-00677000 rw-p 00000000 00:00 0 
00677000-0068a000 r-xp 00000000 08:02 523462     /lib/libz.so.1.2.3.3
0068a000-0068b000 r--p 00012000 08:02 523462     /lib/libz.so.1.2.3.3
0068b000-0068c000 rw-p 00013000 08:02 523462     /lib/libz.so.1.2.3.3
08048000-08085000 r-xp 00000000 08:02 1841075    /root/workspace/AMSERVER/Debug/AMSERVER
08085000-08086000 r--p 0003c000 08:02 1841075    /root/workspace/AMSERVER/Debug/AMSERVER
08086000-08087000 rw-p 0003d000 08:02 1841075    /root/workspace/AMSERVER/Debug/AMSERVER
08087000-080e2000 rw-p 00000000 00:00 0          [heap]
53500000-53525000 rw-p 00000000 00:00 0 
53525000-53600000 ---p 00000000 00:00 0 
536e7000-5371c000 r--s 00000000 08:02 2100420    /var/cache/nscd/services
5371c000-5371d000 ---p 00000000 00:00 0 
5371d000-53f1d000 rw-p 00000000 00:00 0 
53f1d000-53f1e000 ---p 00000000 00:00 0 
53f1e000-5471e000 rw-p 00000000 00:00 0 
5471e000-5471f000 ---p 00000000 00:00 0 
5471f000-54f1f000 rw-p 00000000 00:00 0 
54f1f000-54f20000 ---p 00000000 00:00 0 
54f20000-55720000 rw-p 00000000 00:00 0 
55720000-55721000 ---p 00000000 00:00 0 
55721000-55f21000 rw-p 00000000 00:00 0 
55f21000-55f22000 ---p 00000000 00:00 0 
55f22000-56722000 rw-p 00000000 00:00 0 
56722000-56723000 ---p 00000000 00:00 0 
56723000-56f23000 rw-p 00000000 00:00 0 
56f23000-56f24000 ---p 00000000 00:00 0 
56f24000-57724000 rw-p 00000000 00:00 0 
57724000-57725000 ---p 00000000 00:00 0 
57725000-57f25000 rw-p 00000000 00:00 0 
57f25000-57f26000 ---p 00000000 00:00 0 
57f26000-58726000 rw-p 00000000 00:00 0 
58726000-58727000 ---p 00000000 00:00 0 
58727000-58f27000 rw-p 00000000 00:00 0 
58f27000-58f28000 ---p 00000000 00:00 0 
58f28000-59728000 rw-p 00000000 00:00 0 
59728000-59729000 ---p 00000000 00:00 0 
59729000-59f29000 rw-p 00000000 00:00 0 
59f29000-59f2a000 ---p 00000000 00:00 0 
59f2a000-5a72a000 rw-p 00000000 00:00 0 
5a72a000-5a72b000 ---p 00000000 00:00 0 
5a72b000-5af2b000 rw-p 00000000 00:00 0 
5af2b000-5af2c000 ---p 00000000 00:00 0 
5af2c000-5b72c000 rw-p 00000000 00:00 0 
5b72c000-5b72d000 ---p 00000000 00:00 0 
5b72d000-5bf2d000 rw-p 00000000 00:00 0 
5bf2d000-5bf2e000 ---p 00000000 00:00 0 
5bf2e000-5c72e000 rw-p 00000000 00:00 0 
5c72e000-5c72f000 ---p 00000000 00:00 0 
5c72f000-5cf2f000 rw-p 00000000 00:00 0 
5cf2f000-5cf30000 ---p 00000000 00:00 0 
5cf30000-5d730000 rw-p 00000000 00:00 0 
5d730000-5d731000 ---p 00000000 00:00 0 
Program received signal SIGABRT, Aborted.
[Switching to Thread 0xb6fe2b70 (LWP 1322)]
0x0012d422 in __kernel_vsyscall ()


Program description:
more than 100 threads, more than 10 connections per second and each of connection needs execution some queries on mysql.

Any help is appreciated

---

### Post by dwhitney67 on 2010-10-03
> **hosseinyounesi said:**
> Any help is appreciated
Keep on track... it looks like you are very close to solving this problem!

---

### Post by hosseinyounesi on 2010-10-03
Has anyone used mysqlpp? I'm using it several threads and each of them has it's object. :confused:

---

### Post by dwhitney67 on 2010-10-03
> **hosseinyounesi said:**
> Has anyone used mysqlpp? I'm using it several threads and each of them has it's object. :confused:

I have.

---

### Post by hosseinyounesi on 2010-10-03
This is how I use it:

```
Connection conn(false);

conn.connect(dbname, dbhost, dbuser, dbpass)

Query query = conn.query();
query<< "A QUERY";
query.parse();
if (mysqlpp::StoreQueryResult SessionRes = query.store(computer_id,user_id) )
{
    ....
}
```

That's it. But in several threads and simultaneously. Am I wrong?

---

### Post by worseisworser on 2010-10-03
Perhaps [http://dev.mysql.com/doc/refman/5.1/en/c-thread-functions.html](http://dev.mysql.com/doc/refman/5.1/en/c-thread-functions.html) is of help ...

---

### Post by dwhitney67 on 2010-10-03
Please post the complete code where you are setting up the mysqlpp connection, and performing the query.

What I am expecting to see is that you have that code within a try-catch block, to catch any possible exceptions that may be thrown.

Also, post your code using CODE tags.

---

### Post by hosseinyounesi on 2010-10-03
The code I posted is my real code:

```

Connection conn(false);

conn.connect(dbname, dbhost, dbuser, dbpass)

Query query = conn.query();
query<< "SELECT * from tbl...";//queries are correct and there are lot's of different queries and all are tested
query.parse();
if (mysqlpp::StoreQueryResult SessionRes = query.store(computer_id,user_id) )
{
    //Unrelated to mysql and mysqlpp
    //some mathematical operations
}

```

is mysqlpp thread-safe?

---

### Post by Some Penguin on 2010-10-03
Have you checked the mysql++ documentation?  It's answered there.

[http://tangentsoft.net/mysql++/doc/html/userman/threads.html]("http://tangentsoft.net/mysql++/doc/html/userman/threads.html")

---

### Post by dwhitney67 on 2010-10-03
> **hosseinyounesi said:**
> The code I posted is my real code:

You should guard against unforeseen failures.  For example:
```

   try
   {
      mysqlpp::Connection       dbconn(database.c_str(), host.c_str(), user.c_str(), password.c_str());
      mysqlpp::Query            query = dbconn.query();
      mysqlpp::StoreQueryResult result = query.store(thequery.c_str());

      if (result)
      {
         doSomethingWithResult(result);

         while (query.more_results())
         {
            doSomethingWithResult(query.store_next());
         }
      }
      else
      {
         // some queries do not return results; yet by being here
         // we know that the query was successful.
      }
   }
   catch (std::exception& e)
   {
      std::cerr << "Caught exception: " << e.what() << std::endl;
   }

```

> **hosseinyounesi said:**
> 
is mysqlpp thread-safe?

The link provided by Some Penguin offers good advice on this subject.

---

### Post by hosseinyounesi on 2010-10-04
I replaced libmysqlclient.so with libmysqlclient_r.so and now it's working fine! No change in mysqlpp code or my code in using mysqlpp. What's the difference between 2 these files?!!!

Thanks b4

---

### Post by dwhitney67 on 2010-10-04
> **hosseinyounesi said:**
> I replaced libmysqlclient.so with libmysqlclient_r.so and now it's working fine! No change in mysqlpp code or my code in using mysqlpp. What's the difference between 2 these files?!!!

Thanks b4

It seems that you did not read the documentation carefully enough.
> 
If you use a binary distribution of MySQL on Unixy systems, you usually get two different versions of the MySQL C API library, one with thread support and one without. These are typically called libmysqlclient and libmysqlclient_r, the latter being the thread-safe one. (The &#8220;_r&#8221; means reentrant.)

Did you not read about the ConnectionPool?  You had better be using that too, since from what you described earlier, you have lots of connections in many different threads.

---

