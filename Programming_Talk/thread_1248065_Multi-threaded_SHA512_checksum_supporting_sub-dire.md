---
title: "Multi-threaded SHA512 checksum supporting sub-directories"
date: 2009-08-23
forum: Programming Talk
---

### Post by palmboy5 on 2009-08-23
Apparently such a program doesn't exist since NO ONE bothered to reply to my thread asking about it.
[http://ubuntuforums.org/showthread.php?t=1226008](http://ubuntuforums.org/showthread.php?t=1226008)

So.. I'm going to try writing one myself. It will be written with SHA512 in mind but my design plan should be pretty compatible between the algorithms.

One question I have right now:
What is something in C/C++ that I can use to find out how many logical CPUs the system has?

---

### Post by Reiger on 2009-08-23
I am not sure what the problem really is, because various programs will happily & recursively list all files in a given directory with full paths. Then you can compute a SHA 512 of each file.

If you want you can cat various files together then compute a SHA 512 of the blobs you get.

Alternatively you can tar up a directory and compute a SHA 512 of that.

...

---

### Post by palmboy5 on 2009-08-23
> **Reiger said:**
> I am not sure what the problem really is, because various programs will happily & recursively list all files in a given directory with full paths. Then you can compute a SHA 512 of each file.

Could you list the names of some of those programs, please? :razz: I'm not a linux user so I am unfamiliar with what's available.

By problem, you mean how sha512sum is unable to go into sub-directories? Well, solving that still leaves out multi-threadedness from the program, so.. My problem was, what C/C++ code would tell me how many logical CPUs the system had? I was just going to run <# of CPU or parameter specified> number of sha512sum to work on all the files within the specified folder. For now I can just depend on the parameter, but an answer to my question would be nice.

> **Reiger said:**
> If you want you can cat various files together then compute a SHA 512 of the blobs you get.

Alternatively you can tar up a directory and compute a SHA 512 of that.
I saw both those suggestions during my search for an existing program, and to be honest.. I laughed out loud at the thought of how crude **and still not multi-threaded** those methods were. The netbook Atom CPUs are pretty much the ONLY single-threaded CPUs still in production, so why still think of single-threaded methods?! ](*,)

---

### Post by stroyan on 2009-08-23
You can use sysconf() to inquire the number of processors in linux.
While sysconf() is posix standard, the feature that reports processor counts is not standard.
```

#include <stdio.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
	printf("There are %d processors configured and %d processors available\n",
		sysconf(_SC_NPROCESSORS_CONF), sysconf(_SC_NPROCESSORS_ONLN));
	return 0;
}

```

---

### Post by palmboy5 on 2009-08-24
Thanks! That looks great, but since you said its not standard, can I at least assume the Ubuntu distro will always have "_SC_NPROCESSORS_ONLN"?

---

### Post by Reiger on 2009-08-24
There is **find**, as well as **ls** and both will happily recursively list directories.

You can **fork** off processes in shell scripts, and you can **pipe** the output of above tools to a file which can be **cut** into equal sizes (you would want to prepare more jobs than there are actual cores so that if one job should finish sooner than another you can continue with the next without waiting for the other to complete). As a matter of fact **find** can execute a command/script/program per file as well...

Obtaining hardware information can be done by examining **lshw** although it is not very suitable for on-the-fly adjustments because it dumps a lot of info. There are probably other and more suitable utils for the job though.

---

### Post by Reiger on 2009-08-24
> **palmboy5 said:**
> I saw both those suggestions during my search for an existing program, and to be honest.. I laughed out loud at the thought of how crude **and still not multi-threaded** those methods were. The netbook Atom CPUs are pretty much the ONLY single-threaded CPUs still in production, so why still think of single-threaded methods?! ](*,)

Computing a SHA 512 of a large file should be much less complex (in the sense of algorithmic complexity) than computing the SHA 512 of many small(er) ones. Consequentially computing the SHA 512 of a tar'ed up directory or cat'ed files may very well be far more efficient even if the bottle neck (SHA 512 computation) is/remains single threaded.

EDIT: Plus you can apply compression for bonus efficiency points.

---

### Post by WitchCraft on 2009-08-24
include threading .h in your executable,
and add this code:

```

void* AimBotThread(void* vptr_args)
{
   [COLOR="Red"]  // Code to calculate HASH here[/COLOR]
}

```


In your main program, start the thread:
```

	Cross_Platform_Thread* ptrAimBotThread = new Cross_Platform_Thread(AimBotThread) ;
	ptrAimBotThread->RunAsThread();

```

You must include threading.h

Oh, and if you don't compile to a shared library, you must link to pthread:
**[COLOR="Red"]g++ main.cpp -o main -lpthread[/COLOR]**

Here it is:
threading.h
```


#ifndef _threading_H_
#define _threading_H_



#if ( defined (_WIN32) || defined (_WIN64) || defined (_WINDOWS) )
	#define WIN32_LEAN_AND_MEAN
	#define WIN64_LEAN_AND_MEAN

	#include <windows.h>
	typedef void* (*ptr_ThreadProcType_t)( void* vptr_args );
	typedef DWORD Cross_Platform_Thread_t;
#else // POSIX
	#include "pthread.h"

	typedef pthread_t Cross_Platform_Thread_t;
	typedef void* (*ptr_ThreadProcType_t)( void* vptr_args );

#endif


class Cross_Platform_Thread
{
	private:

		ptr_ThreadProcType_t     m_Callback ;
		Cross_Platform_Thread_t	 m_Threadid ;


#if ( defined (_WIN32) || defined (_WIN64) )
		unsigned long	lng_Timeout;
		HANDLE			hptrThread;
#endif
		void StopThread();

	public:
			Cross_Platform_Thread(ptr_ThreadProcType_t ptrCallback = NULL, unsigned long uslng_TimeOut = 3000);
			virtual ~Cross_Platform_Thread() throw();

			void SetThreadProc(ptr_ThreadProcType_t ptrCallback);
/*
			Cross_Platform_Thread_t FuncGetThreadID()
			{
				return m_Threadid;
			}
*/

			bool RunAsThread();
			bool ThreadExists();
};





Cross_Platform_Thread::Cross_Platform_Thread(ptr_ThreadProcType_t ptrCallback, unsigned long uslng_TimeOut) : m_Callback(ptrCallback), m_Threadid(0)
#if ( defined (_WIN32) || defined (_WIN64) )
, lng_Timeout(uslng_TimeOut), hptrThread(NULL)
#endif
{}


Cross_Platform_Thread::~Cross_Platform_Thread() throw()
{
	StopThread();
}


void Cross_Platform_Thread::StopThread()
{
#if ( defined (_WIN32) || defined (_WIN64) )
	//waiting for the thread to terminate
	if (hptrThread)
	{
		if(WAIT_TIMEOUT == ::WaitForSingleObject (hptrThread, lng_Timeout))
			::TerminateThread (hptrThread, 1);

		::CloseHandle (hptrThread);
	}
#endif
}



bool Cross_Platform_Thread::RunAsThread()
{
	bool bRetVal = false;

	do
	{
		if(ThreadExists())
			break;

#if ( defined (_WIN32) || defined (_WIN64) )

		hptrThread = ::CreateThread (NULL, 0, (unsigned long (__stdcall*) (void*) ) m_Callback, NULL, 0, &m_Threadid);
		if(NULL == hptrThread)
			break;
#else
	    pthread_attr_t attr;

		// Initialize and set thread detached attribute
		pthread_attr_init(&attr);
		pthread_attr_setdetachstate(&attr, PTHREAD_CREATE_DETACHED);

		if( !pthread_create(&m_Threadid, &attr, m_Callback, (void*) this) )
			break;

	   // Free attribute and wait
		pthread_attr_destroy(&attr);
#endif

		bRetVal = true;
	} while(false);

	return bRetVal;
}


void Cross_Platform_Thread::SetThreadProc(ptr_ThreadProcType_t ptrCallback)
{
	m_Callback = ptrCallback;
}



bool Cross_Platform_Thread::ThreadExists()
{
	return m_Threadid ? true : false;
}

#endif // _threading_H_


```

---

### Post by Quikee on 2009-08-25
> **palmboy5 said:**
> I saw both those suggestions during my search for an existing program, and to be honest.. I laughed out loud at the thought of how crude **and still not multi-threaded** those methods were. The netbook Atom CPUs are pretty much the ONLY single-threaded CPUs still in production, so why still think of single-threaded methods?! ](*,)

Actually in this case doing checksum in parallel just might not do any good at all. The problem is that the bottleneck is not the CPU but the hard disk and if you will calculate the checksum on more files in parallel, the hard disk will have to seek from one file to another and all the parallel performance benefits that one expects would be lost.

From my experience sometimes seemingly crude methods in the end turn out to be the best methods.

Anyway.. to write a program in python that would do this in parallel should be pretty easy. hashlib module has support for sha512 out of the box, multiprocessing module to do things in multiple processes and os.walk to walk the directories recursively.

---

### Post by leblancmeneses on 2009-08-25
you need to coordinate your threads so you assemble a file that will eventually be hashed.. so you end up having to do threads.join()  and blocking until each branch is complete.

also if you have a large branch of folders.. and you create threads in each you end up having more context switching then actual work being done.

as others have eluded .. a program like this does not exist because of the snow ball of limits that exist in both hardware/software. (do it sequentially)

>[WitchCraft]("http://ubuntuforums.org/member.php?u=503084")
i'll have to try your cross platform thread class..
neato

---

### Post by WitchCraft on 2009-08-25
> **leblancmeneses said:**
> 

>[WitchCraft]("http://ubuntuforums.org/member.php?u=503084")
i'll have to try your cross platform thread class..
neato

I've tested it on Windows, and on Linux, it works. 
It is reported to work on Mac OS X, too.

If you want to open up threads for items in a directory structure, you should limit the maximum amount of threads running in parallel, or you could hit the maximum thread limit of the system and crash either the system or your program.

---

### Post by palmboy5 on 2009-08-25
I went ahead and tested multi-threaded performance due to what you guys have been saying.

Tested a folder with 24 same-size files totaling 4.37GB (with no sub-folders :[). To test muliple "threads" I split the checksum file into equal parts and used a script such as
```
time sha512sum -c checksumsunix1.exf &
time sha512sum -c checksumsunix2.exf &
time sha512sum -c checksumsunix3.exf &
time sha512sum -c checksumsunix4.exf &
```
(I could have only put "time" on the last line and taken out the last & as well, but whatever :p)

Atom 330, dual core CPU with Hyperthreading.

Single-threaded test:
Ubuntu (sha512sum -c checksumsunix.exf)
2:05 minutes:seconds

Two-threaded test:
Ubuntu (script)
3:37

Four-threaded test:
Ubuntu (script)
3:39 (Looks like Hyperthreading didn't help at all.)

Alright, I guess I'll keep it single-threaded. I'm still going to make the program, though, for other stuff in addition to sub-directory capability. For example, I'd like the option to update a particular file's checksum within the digest file if I know that particular file was modified. Doing such a thing manually is too bothersome. I definitely want individual file checksums, and for that reason, checksumming full tar files and blobs of cat are unacceptable options.

---

### Post by Quikee on 2009-08-26
> **palmboy5 said:**
> 
Alright, I guess I'll keep it single-threaded. I'm still going to make the program, though, for other stuff in addition to sub-directory capability. For example, I'd like the option to update a particular file's checksum within the digest file if I know that particular file was modified. Doing such a thing manually is too bothersome. I definitely want individual file checksums, and for that reason, checksumming full tar files and blobs of cat are unacceptable options.

Maybe better patch [CFV]("http://cfv.sourceforge.net/") to also support sha512 and updating of digest files.

---

### Post by WitchCraft on 2009-08-26
> **palmboy5 said:**
> I went ahead and tested multi-threaded performance due to what you guys have been saying.

Tested a folder with 24 same-size files totaling 4.37GB (with no sub-folders :[). To test muliple "threads" I split the checksum file into equal parts and used a script such as
```
time sha512sum -c checksumsunix1.exf &
time sha512sum -c checksumsunix2.exf &
time sha512sum -c checksumsunix3.exf &
time sha512sum -c checksumsunix4.exf &
```
(I could have only put "time" on the last line and taken out the last & as well, but whatever :p)

Atom 330, dual core CPU with Hyperthreading.

Single-threaded test:
Ubuntu (sha512sum -c checksumsunix.exf)
2:05 minutes:seconds

Two-threaded test:
Ubuntu (script)
3:37

Four-threaded test:
Ubuntu (script)
3:39 (Looks like Hyperthreading didn't help at all.)



This is not Hyperthreading, this is multithreading. 
Hyperthreading is implemented in the processor, and the compiler/OS needs to support it.

How fast your CPU is or how many cores your CPU has or whether it is using Hyperthreading is irrelevant for the reading speed of the hard disk, at least as long as your CPU is faster than the PCI BUS or the HD controller, which is something that I would assume to be true in general.

And it is logical that your multithreaded version is slower, since the hard drive has not only to read one file, it has to switch back and forth between several locations on disk, each for time for 4 files in 4 threads...

So it becomes degressively slower with each thread that reads from the hard drive, which is just what you describe.

The point of a thread is not to make an operation faster (that's not possible without optimizing your code or switching the compiler), it is to make the program flow asynchronous.
In other words, the point of a thread is that your checksum calculation runs in the background, while your program can continue doing other things (file IO).

And you then have to design your program in a way that its execution speed benefits of this asynchronousness. 
As you have seen, the use of threads can actually slow down a program if the useage of threads is ill-chosen.
When using threads, you simply HAVE to take care of the details.


To actually increase the performance with threads, you have to redesign your program, such as:
get a array of files to check
for each file in the array
check the file size
if the file size is not too large
allocate a memory buffer and read the entire file into it
start a thread calculating the checksum of this memory buffer
int the meanwhile the main program goes to the next file and reads that file and starts the next thread, and so on.

until all files are read

then you have to wait for all threads to complete, and get back each checksum (for example pass an array +index to each thread).

Make sure you don't open up too many threads at any time, and that you're not out of memory at any time.
And switch the compiler optimization options to maximum.

This way it is assured that you only read one file at a time (fastest), and process the file contents in the time that remains when the CPU/BUS is not busy reading the hard drive.
That might require setting program and thread priority, but it should speed up your program considerably.

You see, it's a bit complex, which is why usually one takes the simpler and more reliable way, which unfortunately happens to be slower.
However, you can and will benefit in speed from threads (but only if properly used in the program design), especially if your OS & Compiler supports hyperthreading.

---

