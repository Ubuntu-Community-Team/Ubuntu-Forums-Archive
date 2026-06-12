---
title: "Problem with pthread_create()(C++)"
date: 2007-01-12
forum: Programming Talk
---

### Post by niklas-komani on 2007-01-12
Hey, guys I encountered a strange problem concerning Thread creation.
I'm trying to write a Server where every Client is served by a thread, which to me seems prity effective in my case since I'm using blocking recvs and most of the Threads will stay blocked for most of the time. Now I encountered that after about a few hundred connects of which each starts a thread which in my test cas closes after less then a second due to client disconnect, the Server can't launch new ClientThreads while the accept call still returns valid sockets (It's after 255 attempts on my Debian Sarge Server and at about 380-382 attempts on Ubuntu and Debian Etch). Another crazy problem is that taking pauses of a few secconds between the connection attempts doesn't make any difference. Which excludes race Conditions as the last Thread will be closed when a new one is opned.
Luckily I was able to shrink the problem down to a very small piece of Code:
```

#include <iostream>
#include <pthread.h>

void*  mythread(void* ptr){
        std::cout<<"Thread started"<<std::endl;
        return 0;
}

int main (int argc, char* argv){
for(int i=0;i<500;i++){
        pthread_t MyThread;
        pthread_create(&MyThread, 0, &mythread, 0);
        //sleep(1); Commenting this in doesn't solve the problem
}
        return 0;
}

```

Note: I left out a Mutex for std since the Output is not scattered and this would make the code less simple.(On Mac OS X however std doesn't seem to serliz the Output, but with the sleep commented in this is a not a problem there either)

You can compile the code with "g++ file.cpp -o thread -lpthread"
Then you can run it with "./thread > out.txt" and count the lines of output which should according to the loop be 500 however "grep -c "Thread started" out.txt" only Counts 255 hits on debian sarge and 382 on Etch and Ubuntu.
Can someone please tell me why a process can't open a thread as many times as needed?
Any help will be appreciated!
Cincerly Niklas

---

### Post by angustia on 2007-01-12
1.- try with pthread_detach at the end of mythread()

2.- look in /proc/sys/kernel/threads-max (max number of threads for the whole system)

3- with ps -eLf you can see processes with their threads (under LWP (light weight process))

---

### Post by niklas-komani on 2007-01-12
Thank you very very much, pthread_detach solves the problem. For me that was a really hard bug to track down^^ I think pthread_detach is also not mentioned in most Pthread starter Tutorials. 
Cincerly Niklas

---

### Post by Houman on 2007-01-12
hi there;
I had a quick question, I ran the code and the error value of pthread_create is 12 at the time that it fails (after 382 threads) also the value of threads-max is way higher than 382.

I was wondering why cant the program allocate more than 382 simultanoues threads? Also 
I wasnt able to find out what this error code of 12 means, I read the description of [pthread_create]("http://www.opengroup.org/onlinepubs/007908799/xsh/pthread_create.html") but I dont know how to relate the error value to the enum thats described there;

regards

Houman

---

### Post by niklas-komani on 2007-01-12
Well the Threads don't run concurrent but one after the other, it seems that somehow the System can't handle so many thread starts if the ressources of stopped threads aren't returned but I don't know the exact cause, maybe angustia can shed a little bit of light on this.

---

### Post by niklas-komani on 2007-01-13
Can someone also tell me how many threads my process can run concurrently? I still don't understand why it could only open 380 threads, even when not releasing the ressources this number seems to be prity small.

---

### Post by Houman on 2007-01-13
hi there, 

After much googling I have found a solution to the problem and I think I know what the problem is, but before that, here is some links for people who had the same problems (i got the solution from there):

[http://groups.google.ca/group/comp.programming.threads/browse_thread/thread/76ae8922df444d74/5f4703c0e76d75a5](http://groups.google.ca/group/comp.programming.threads/browse_thread/thread/76ae8922df444d74/5f4703c0e76d75a5)
[http://groups.google.ca/group/comp.programming.threads/browse_thread/thread/561f30b84715161c/cf916998fb24bc31](http://groups.google.ca/group/comp.programming.threads/browse_thread/thread/561f30b84715161c/cf916998fb24bc31)
[http://groups.google.ca/group/comp.programming.threads/browse_thread/thread/dd37f1ba5b61589e/1932b03731a10b0b](http://groups.google.ca/group/comp.programming.threads/browse_thread/thread/dd37f1ba5b61589e/1932b03731a10b0b)

This is the code that I have (and it runs fine without detaching the threads):

```

....
    [COLOR="Red"]pthread_attr_t tattr;
    size_t size; 
    size = SOMESTACKSIZE + PTHREAD_STACK_MIN;
    pthread_attr_init(&tattr); 
    pthread_attr_setstacksize(&tattr, size); [/COLOR]
    
    


    for(int i=0;i<500;i++){
        pthread_t MyThread;
        int output= pthread_create(&MyThread, [COLOR="Red"]&tattr[/COLOR], &mythread, 0);
	
	if (output)
	{
	    std::cout<< "hi  " <<EINVAL <<std::endl; 
	    std::cout<<"error at iteration:  " << i << "   and return code from pthread_create() is  "<<output<<std::endl;
	    std::cout<<"error is " <<strerror(output) <<std::endl;
	    exit(-1);
	}
	....
    
```

The problem is that every new thread has to allocate as much as the stack size , so if your stack size is 8 Mb, then 300 threads would have to allocate 2400 Mb. The solution as I have read in many thread (and as tested if you try the code above) is to "reduce" the stack size. BUT your new stack size should be bigger than PTHREAD_STACK_MIN ( so add whatever arbitrary value to this constant to get your new stack size, but make sure its less than your current stacksize or else you wont obviously get the desired result).

Also I read something about[ NPTL]("http://en.wikipedia.org/wiki/Native_POSIX_Thread_Library"), I have never used it before, but do we have it here on ubuntu :| seems threads run much better when using this library.

Also here is another link for all the possible limitations of creating too many threads:

[http://nptl.bullopensource.org/Tests/NPTL-limits.html#pthread_cr](http://nptl.bullopensource.org/Tests/NPTL-limits.html#pthread_cr)

The problem we were having is the first issue discussed (the stack).

Also I read that it seems its better to make use of thread pools if you need to spawn too many threads, and that the use of too many threads is *sometimes* indicative of a design flaw.

regards

Houman

---

### Post by niklas-komani on 2007-01-13
Thanks for the infos, using "getconf GNU_LIBPTHREAD_VERSION" I just foudn out that Debian is already using NPTL by default so the only thing i have to chaneg to make my Server more effective is reducing the Stacksize, I think I need to detach it though, too. This might be replaceable with another attribute change but I will probably do it with an explicit  call to pthread_detach() because that's easier. I also think that in my case the design of the server doesn't seem to be flawed, though it might still be improveable. Since most Threads will be blocked by recv or accept and ther will probably be only very few running concurrently it's reasonable to use many threads. Former versions of Apache for exampel used one process per connection which involves an even bigger overhead, especially when the Stacksize of a Thread can be reduced. At most I probably need to create about 5000 Threads which should be fine when using small Stacksizes. Since blocked Threads shoudln't create much overhead in the sheduling.

/Edit I designed the Server so that i might implement a Thread pool in the futuere quit easily thanks to some OOP programming which encapsulates all data needed by a ClientThread in an Object.

---

