---
title: "patches? (C/C++)"
date: 2007-12-14
forum: Programming Talk
---

### Post by malfist on 2007-12-14
I have two questions, how do I apply patches to an already compiled source, and two, how to I make patches?

Thanks,
Malfist

---

### Post by swerner on 2007-12-14
It really depends how your patch looks.  Is it a bz file or plain text?  The commands are the same, but there are many options to make/apply patches.  The command to make a patch is 'diff', the command to apply a patch is 'patch'.  This [site]("http://www.cpqlinux.com/patch.html") has some info on patching.  But you may prefer to use the man pages.

---

### Post by malfist on 2007-12-14
It's just plaintext. I'll check that site out.

---

### Post by malfist on 2007-12-14
What would I have to do after applying the patch? Would I have to recompile the whole project or what?

---

### Post by geirha on 2007-12-14
> **malfist said:**
> What would I have to do after applying the patch? Would I have to recompile the whole project or what?

Depends on the project and how the code is put together and such. If the project uses autoconf, it's probably enough to just run "make" which should compile and link the parts related to the patch.

---

### Post by malfist on 2007-12-14
Well, it is a cross platform server app. I'm wondering how it will work. I ask the people who run it.

---

### Post by malfist on 2007-12-27
What about a patchfile that edits more than just one file? I tried applying it but patch just stopped without any output and acted like it was running.

example:```

Index: src/logonserver/LogonConsole.cpp
===================================================================
--- src/logonserver/LogonConsole.cpp	(revision 1987)
+++ src/logonserver/LogonConsole.cpp	(working copy)
@@ -51,6 +51,10 @@
 		Sleep(100);
 	}
 	printf("Console shut down.\n");
+#else
+	_thread->kill = true;
+	ThreadPool.KillThread(_thread);
+	printf("Console shut down.\n");
 #endif
 }
 
@@ -60,26 +64,51 @@
 
 	SetThreadName("Console Interpreter");
 	sLogonConsole._thread = this;
-	int i = 0;
-	char cmd[96];
+	int i = 0, p = 0;
+	char cmd[BUF_SIZE], garbage[1024];
+	int nfds = fileno(stdin) > pfd[0] ? fileno(stdin)+1 : pfd[0]+1;
 
 	while (!kill)
 	{
-		
-		// Make sure our buffer is clean to avoid Array bounds overflow
-		memset(cmd,0,sizeof(cmd)); 
-		// Read in single line from "stdin"
-		fgets(cmd, 80, stdin);
+		int r;
+		fd_set rd;
+		FD_ZERO(&rd);
+		FD_SET(fileno(stdin), &rd);
+		FD_SET(pfd[0], &rd);
+	
+		// Wait for data.
+		r = select(nfds, &rd, NULL, NULL, NULL);
 
+		if (!FD_ISSET(fileno(stdin), &rd) || r == 0 || r == -1)
+			continue;
+
+		// Read in data, if we have room.
+		if (p < BUF_SIZE)
+		{
+			p += read(fileno(stdin), cmd+p, BUF_SIZE-p);
+			if (cmd[p-1] != '\n')
+				continue;
+			else
+				p = 0; // We have a full command.
+		}
+		// Otherwise, junk it and end the command.
+		else
+		{
+			read(fileno(stdin), garbage, sizeof(garbage));
+			cmd[BUF_SIZE-1] = '\n';
+			p = 0;
+		}
+
 		if(kill)
 			break;
 
-		for( i = 0 ; i < 80 || cmd[i] != '\0' ; i++ )
+		for( i = 0 ; i < BUF_SIZE || cmd[i] != '\0' ; i++ )
 		{
 			if( cmd[i] =='\n' )
 			{
 				cmd[i]='\0';
 				sLogonConsole.ProcessCmd(cmd);
+				memset(cmd,0,BUF_SIZE);
 				fflush(stdin);
 				break;
 			}
Index: src/logonserver/LogonConsole.h
===================================================================
--- src/logonserver/LogonConsole.h	(revision 1987)
+++ src/logonserver/LogonConsole.h	(working copy)
@@ -23,6 +23,8 @@
 #include "Common.h"
 #include "../game/CThreads.h"
 
+#define BUF_SIZE 80
+
 class LogonConsoleThread : public ThreadBase
 {
 public:
Index: src/logonserver/Main.cpp
===================================================================
--- src/logonserver/Main.cpp	(revision 1987)
+++ src/logonserver/Main.cpp	(working copy)
@@ -331,11 +331,8 @@
 	delete sl;
 	delete cl;
 	sSocketMgr.CloseAll();
-#ifdef WIN32
 	sSocketMgr.ShutdownThreads();
-#endif
 	sLogonConsole.Kill();
-	delete LogonConsole::getSingletonPtr();
 
 	// kill db
 	sLog.outString("Waiting for database to close..");
@@ -344,6 +341,7 @@
 	delete sLogonSQL;
 
 	ThreadPool.Shutdown();
+	delete pfc;
 
 	// delete pid file
 	remove("logonserver.pid");
@@ -353,6 +351,7 @@
 	delete IPBanner::getSingletonPtr();
 	delete SocketMgr::getSingletonPtr();
 	delete SocketGarbageCollector::getSingletonPtr();
+	delete LogonConsole::getSingletonPtr();
 	printf("Shutdown complete.\n");
 }
 
Index: src/logonserver/PeriodicFunctionCall_Thread.h
===================================================================
--- src/logonserver/PeriodicFunctionCall_Thread.h	(revision 1987)
+++ src/logonserver/PeriodicFunctionCall_Thread.h	(working copy)
@@ -43,7 +43,7 @@
 		uint32 end;
 		uint32 etime;
 		// initial rest
-		Sleep(interval);
+		ThreadSleep(interval);
 
 		while(running && mrunning)
 		{
@@ -55,7 +55,7 @@
 			end = getMSTime();
 			etime = end - start;
 			if(etime < interval)
-				Sleep(interval - etime);
+				ThreadSleep(interval - etime);
 		}
 #else
 		thread_active=true;
@@ -89,6 +89,9 @@
 			Sleep(100);
 		}
 		printf(" done.\n");
+#else
+		/* Don't wait for the thread to wake up again. Just kill it. */
+		ThreadPool.KillThread(this);
 #endif
 	}
 
Index: src/shared/Network/SocketMgrLinux.cpp
===================================================================
--- src/shared/Network/SocketMgrLinux.cpp	(revision 1987)
+++ src/shared/Network/SocketMgrLinux.cpp	(working copy)
@@ -68,11 +68,35 @@
             fds[i]->Delete();
 }
 
+void SocketMgr::ShutdownThreads()
+{
+    SocketWorkerThread * w;
+    while(workers.size() > 0)
+    {
+	w = *workers.begin();
+
+	struct epoll_event ev;
+	memset(&ev, 0, sizeof(epoll_event));
+	ev.events = EPOLLIN;
+	ev.data.fd = w->pfd[0];
+    	/* Add the worker's signal fd so that it catches it's kill signal. */
+	epoll_ctl(epoll_fd, EPOLL_CTL_ADD, ev.data.fd, &ev);
+
+	workers.erase(w);
+	w->kill = true;
+	ThreadPool.KillThread(w);
+    }
+}
+
 void SocketMgr::SpawnWorkerThreads()
 {
     uint32 count = 1;
     for(uint32 i = 0; i < count; ++i)
-        ThreadPool.ExecuteTask(new SocketWorkerThread());
+    {
+	SocketWorkerThread * w = new SocketWorkerThread();
+	workers.insert(w);
+	ThreadPool.ExecuteTask(w);
+    }
 }
 
 bool SocketWorkerThread::run()
@@ -83,11 +107,15 @@
     struct epoll_event ev;
     SocketMgr * mgr = SocketMgr::getSingletonPtr();
 
-    while(true)
+    while(!kill)
     {
         fd_count = epoll_wait(mgr->epoll_fd, events, THREAD_EVENT_SIZE, 5000);
         for(i = 0; i < fd_count; ++i)
         {
+	    if(events[i].data.fd == pfd[0] && events[i].events & EPOLLIN) {
+	    	Log.Debug("SocketWorkerThread", "Received kill signal.");
+	    	break; // We received our kill signal.
+	    }
             if(events[i].data.fd >= SOCKET_HOLDER_SIZE)
             {
                 Log.Warning("epoll", "Requested FD that is too high (%u)", events[i].data.fd);
Index: src/shared/Network/SocketMgrLinux.h
===================================================================
--- src/shared/Network/SocketMgrLinux.h	(revision 1987)
+++ src/shared/Network/SocketMgrLinux.h	(working copy)
@@ -36,6 +36,8 @@
     /// socket counter
     int socket_count;
 
+    std::set<SocketWorkerThread*> workers;
+
 public:
 
     /// friend class of the worker thread -> it has to access our private resources
@@ -79,6 +81,9 @@
     /// closes all sockets
     void CloseAll();
 
+    /// shutdown worker threads
+    void ShutdownThreads();
+
     /// spawns worker threads
     void SpawnWorkerThreads();
 };
@@ -89,6 +94,11 @@
     struct epoll_event events[THREAD_EVENT_SIZE];
 
 public:
+    bool kill;
+    SocketWorkerThread()
+    {
+    	kill = false;
+    }
     bool run();
 };
 
Index: src/shared/Threading/ThreadPool.cpp
===================================================================
--- src/shared/Threading/ThreadPool.cpp	(revision 1987)
+++ src/shared/Threading/ThreadPool.cpp	(working copy)
@@ -218,6 +218,41 @@
 	_mutex.Release();
 }
 
+void CThreadPool::SignalThread(ThreadBase * ExecutionTarget, int sig)
+{
+	_mutex.Acquire();
+	for (ThreadSet::iterator itr = m_activeThreads.begin();
+			itr != m_activeThreads.end(); ++itr) {
+		if ((uint32)(*itr)->ExecutionTarget ==
+				(uint32)ExecutionTarget) {
+			Log.Notice("ThreadPool",
+				   "Sending signal %d to thread %u.", sig,
+				   (*itr)->ControlInterface.GetId());
+#ifndef WIN32
+#include <signal.h>
+			if (write(ExecutionTarget->pfd[1], &sig, sizeof(sig))
+					!= sizeof(sig)) {
+				Log.Error("ThreadPool",
+					  "Failed to signal thread %u.",
+					  (*itr)->ControlInterface.GetId());
+			} else if (sig == SIGTERM || sig == SIGKILL) {
+				++_threadsToExit;
+			}
+#endif
+			break;
+		}
+	}
+	_mutex.Release();
+	return;
+}
+
+void CThreadPool::KillThread(ThreadBase * ExecutionTarget)
+{
+#ifdef WIN32
+#else
+	SignalThread(ExecutionTarget, SIGKILL);
+#endif
+}
 void CThreadPool::Shutdown()
 {
 	_mutex.Acquire();
@@ -238,7 +273,7 @@
 		_mutex.Acquire();
 		if(m_activeThreads.size() || m_freeThreads.size())
 		{
-			Log.Debug("ThreadPool", "%u threads remaining...",m_activeThreads.size() + m_freeThreads.size() );
+			Log.Debug("ThreadPool", "%u active and %u free threads remaining...",m_activeThreads.size(),m_freeThreads.size() );
 			_mutex.Release();
 			Sleep(1000);
 			continue;
Index: src/shared/Threading/ThreadStarter.h
===================================================================
--- src/shared/Threading/ThreadStarter.h	(revision 1987)
+++ src/shared/Threading/ThreadStarter.h	(working copy)
@@ -20,11 +20,67 @@
 #ifndef _THREADING_STARTER_H
 #define _THREADING_STARTER_H
 
+#include "../NGLog.h"
+
+#ifndef WIN32
+#include <sys/select.h>
+#include <sys/time.h>
+#include <sys/types.h>
+#include <unistd.h>
+#endif
+
 class SERVER_DECL ThreadBase
 {
 public:
-	ThreadBase() {}
+#ifdef WIN32
+	ThreadBaes() {}
 	virtual ~ThreadBase() {}
+#else
+	/* Signal pipe. */
+	int pfd[2];
+
+	ThreadBase()
+	{
+		ASSERT(pipe(pfd) == 0);
+	}
+
+	virtual ~ThreadBase()
+	{
+		close(pfd[0]);
+		close(pfd[1]);
+	}
+
+	/* Sleep, but wake up on signals.
+	 * Returns 0 if thread slept for the requested duration, -1 on error,
+	 * or the signal number that woke it up. */
+	int ThreadSleep(int millisec)
+	{
+		struct timeval timeout;
+		int r;
+		fd_set rd;
+
+		FD_ZERO(&rd);
+		FD_SET(pfd[0], &rd);
+		timeout.tv_sec = millisec/1000;
+		timeout.tv_usec = (millisec%1000)*1000;
+
+		r = select(pfd[0]+1, &rd, NULL, NULL, &timeout);
+
+		if (r == -1) {
+			perror("ThreadBase::Sleep() - select()");
+			return -1;
+		} else if (FD_ISSET(pfd[0], &rd)) {
+			int sig = -1;
+			if (read(pfd[0], &sig, sizeof(sig)) > 0)
+				Log.Debug("ThreadBase::Sleep",
+					  "Woke up via signal %d", sig);
+			return sig;
+		}
+
+		/* We slept for the requested duration. */
+		return 0;
+	}
+#endif
 	virtual bool run() = 0;
 	virtual void OnShutdown() {}
 #ifdef WIN32
Index: src/shared/Threading/ThreadPool.h
===================================================================
--- src/shared/Threading/ThreadPool.h	(revision 1987)
+++ src/shared/Threading/ThreadPool.h	(working copy)
@@ -67,6 +67,7 @@
 
 #else
 #include <semaphore.h>
+#include <pthread.h>
 int GenerateThreadId();
 
 class ThreadController
@@ -160,6 +161,12 @@
 	// kills x free threads
 	void KillFreeThreads(uint32 count);
 
+	// send a signal to a thread
+	void SignalThread(ThreadBase * ExecutionTarget, int sig);
+
+	// kills a given thread
+	void KillThread(ThreadBase * ExecutionTarget);
+
 	// resets the gobble counter
 	inline void Gobble() { _threadsEaten=(int32)m_freeThreads.size(); }
 
Index: src/game/DayWatcherThread.cpp
===================================================================
--- src/game/DayWatcherThread.cpp	(revision 1987)
+++ src/game/DayWatcherThread.cpp	(working copy)
@@ -41,6 +41,8 @@
 	m_running = false;
 #ifdef WIN32
 	SetEvent(m_abortEvent);
+#else
+	ThreadPool.KillThread(this);
 #endif
 }
 
@@ -159,7 +161,7 @@
 #ifdef WIN32
 		WaitForSingleObject(m_abortEvent, 120000);
 #else
-		Sleep(120000);
+		ThreadSleep(120000);
 #endif
 		if(!m_running)
 			break;
Index: src/ascent/CConsole.cpp
===================================================================
--- src/ascent/CConsole.cpp	(revision 1987)
+++ src/ascent/CConsole.cpp	(working copy)
@@ -57,6 +57,10 @@
 		Sleep(100);
 	}
 	printf("Console shut down.\n");
+#else
+	_thread->kill = true;
+	ThreadPool.KillThread(_thread);
+	printf("Console shut down.\n");
 #endif
 }
 bool CConsoleThread::run()
@@ -64,24 +68,51 @@
 	SetThreadName("Console Interpreter");
 	sCConsole._thread = this;
 	size_t i = 0;
-	char cmd[96];
+	int p = 0;
+	char cmd[BUF_SIZE], garbage[1024];
+	int nfds = fileno(stdin) > pfd[0] ? fileno(stdin)+1 : pfd[0]+1;
 
 	while (kill != true)
 	{
-		// Make sure our buffer is clean to avoid Array bounds overflow
-		memset(cmd,0,sizeof(cmd)); 
-		// Read in single line from "stdin"
-		fgets(cmd, 80, stdin);
+		int r;
+		fd_set rd;
+		FD_ZERO(&rd);
+		FD_SET(fileno(stdin), &rd);
+		FD_SET(pfd[0], &rd);
 
+		// Wait for data.
+		r = select(nfds, &rd, NULL, NULL, NULL);
+
+		if (!FD_ISSET(fileno(stdin), &rd) || r == 0 || r == -1)
+			continue;
+
+		// Read in data, if we have room.
+		if (p < BUF_SIZE)
+		{
+			p += read(fileno(stdin), cmd+p, BUF_SIZE-p);
+			if (cmd[p-1] != '\n')
+				continue;
+			else
+				p = 0; // We have a full command.
+		}
+		// Otherwise, junk it and end the command.
+		else
+		{
+			read(fileno(stdin), garbage, sizeof(garbage));
+			cmd[BUF_SIZE-1] = '\n';
+			p = 0;
+		}
+
 		if(kill)
 			break;
 
-		for( i = 0 ; i < 80 || cmd[i] != '\0' ; i++ )
+		for( i = 0 ; i < BUF_SIZE || cmd[i] != '\0' ; i++ )
 		{
 			if( cmd[i] =='\n' )
 			{
 				cmd[i]='\0';
 				sCConsole.ProcessCmd(cmd);
+				memset(cmd,0,sizeof(cmd)); 
 				fflush(stdin);
 				break;
 			}
Index: src/ascent/CConsole.h
===================================================================
--- src/ascent/CConsole.h	(revision 1987)
+++ src/ascent/CConsole.h	(working copy)
@@ -23,6 +23,8 @@
 #include "Common.h"
 #include "../game/CThreads.h"
 
+#define BUF_SIZE 80
+
 class CConsoleThread : public ThreadBase
 {
 public:
Index: src/ascent/Master.cpp
===================================================================
--- src/ascent/Master.cpp	(revision 1987)
+++ src/ascent/Master.cpp	(working copy)
@@ -462,9 +462,7 @@
 	ls->Close();
 	delete ls;
 #endif
-#ifdef WIN32
 	sSocketMgr.ShutdownThreads();
-#endif
 	sSocketMgr.CloseAll();
 
 	// begin server shutdown
```

---

### Post by samjh on 2007-12-27
Can you copy and paste the console output when you run the patch command?

Usually if a patch fails, it will tell you there is a problem, and produce a file with the rejected code.

---

### Post by malfist on 2007-12-27
This is a different patch but from the same guy and it is multiplule lines too. It does this:
```

patch --verbose freebsdShutdown.patch 


```
And then it stops and does nothing, no exit or anything.

edit: Nevermind, my bad, I wasn't using patch right. Sorry to bother you people.

---

### Post by geirha on 2007-12-27
try:
```
patch <freebsdShutdown.patch
```
it expects the patch on stdin. You might have to add -p0,  -p1 or similar to the patch command, depending on where in the source tree you're at when you're running it.

---

### Post by engla on 2007-12-28
*patch* is IMO a pretty dumb utility, since it can stop halfway if the patch does not apply. So you always do a check first
```
patch -p0 --dry-run < patchfile.patch
```
And then if it applies cleanly you can take away --dry-run. The -p0 option depends on the patch and perhaps it should be -p1.

---

### Post by swerner on 2007-12-28
Yes, patch is not all that friendly, like anything in Unix, no message is a good thing, it means there have been no errors.

Yes, patch will work on more than one file at once.

---

