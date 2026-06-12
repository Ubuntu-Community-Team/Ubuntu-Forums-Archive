---
title: "what is stale pid file"
date: 2010-05-28
forum: Programming Talk
---

### Post by tapas_mishra on 2010-05-28
Hi,
 I want to know what is stale pid file how can I find that from error logs.Or how can I get to know it if there is some problem I had a similar problem but I could not get the idea unless some one remotely logged in to my server and deleted that file.
 I do not have any clue of this problem and I did google that [http://www.google.co.in/search?hl=en&safe=active&q=what+is+stale+pid+file&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.co.in/search?hl=en&safe=active&q=what+is+stale+pid+file&aq=f&aqi=&aql=&oq=&gs_rfai=)
but did not got any thing helpful.
I am also posting a log if some one wishes to see and let me know to understand this concept

```

2009-10-20T20:09:33 daemonizing the process 
2009-10-20T20:09:33 set current directory: '/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zeoserver' 
2009-10-20T20:09:33 daemon manager started 
2009-10-20T20:09:33 spawned process pid=17397 
2009-10-20T20:09:33 (17397) created PID file '/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/var/zeoserver.pid' 
2009-10-20T20:09:33 (17397) opening storage '1' using FileStorage 
2009-10-20T20:09:33 (17397) StorageServer created RW with storages: 1:RW:/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/var/filestorage/Data.fs 
2009-10-20T20:09:33 (17397) listening on ('127.0.0.1', 8100) 
2009-10-20T20:09:52 (17397) new connection ('127.0.0.1', 50127): <ManagedServerConnection ('127.0.0.1', 50127)> 
2009-10-20T20:09:52 (127.0.0.1:50127) received handshake 'Z303' 
2009-10-20T20:09:52 (127.0.0.1:50127) loadEx() raised exception: 0x00 
Traceback (most recent call last): 
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZEO/zrpc/connection.py", line 535, in handle_request 
    ret = meth(*args) 
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZEO/StorageServer.py", line 254, in loadEx 
    return self.storage.loadEx(oid, version) 
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZODB/FileStorage/FileStorage.py", line 523, in loadEx 
    pos = self._lookup_pos(oid) 
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZODB/FileStorage/FileStorage.py", line 514, in _lookup_pos 
    raise POSKeyError(oid) 
POSKeyError: 0x00 
2009-10-20T20:11:47 (17397/127.0.0.1:50127) disconnected 
2009-10-20T20:11:48 (17397) terminated by SIGTERM 
2009-10-20T20:11:48 (17397) closing storage '1' 
2009-10-20T20:11:48 (17397) removed PID file '/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/var/zeoserver.pid' 
2009-10-20T20:11:48 pid 17397: exit status 0 
2009-10-20T20:11:48 Exiting 
2010-05-25T19:27:22 daemonizing the process 
2010-05-25T19:27:22 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-25T19:27:22 daemon manager started 
2010-05-25T19:27:22 spawned process pid=2542 
2010-05-25T19:27:22 (2542) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-25T19:27:22 (2542) opening storage '1' using FileStorage 
2010-05-25T19:27:22 (2542) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-25T19:27:22 (2542) listening on ('127.0.0.1', 8100) 
2010-05-25T19:27:32 (2542) new connection ('127.0.0.1', 46505): <ManagedServerConnection ('127.0.0.1', 46505)> 
2010-05-25T19:27:32 (127.0.0.1:46505) received handshake 'Z303' 
2010-05-25T19:34:03 daemon manager killed by SIGTERM 
2010-05-25T19:34:03 (2542) terminated by SIGTERM 
2010-05-25T19:34:03 (2542) closing storage '1' 
2010-05-25T19:34:03 (2542) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-25T19:35:09 daemonizing the process 
2010-05-25T19:35:09 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-25T19:35:09 daemon manager started 
2010-05-25T19:35:09 spawned process pid=2145 
2010-05-25T19:35:09 (2145) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-25T19:35:09 (2145) opening storage '1' using FileStorage 
2010-05-25T19:35:09 (2145) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-25T19:35:09 (2145) listening on ('127.0.0.1', 8100) 
2010-05-25T19:35:19 (2145) new connection ('127.0.0.1', 51546): <ManagedServerConnection ('127.0.0.1', 51546)> 
2010-05-25T19:35:19 (127.0.0.1:51546) received handshake 'Z303' 
2010-05-27T11:16:55 Unlinking stale socket /opt/eduCommons-3.2.1/var/zeo.zdsock; sleep 1 
2010-05-27T11:16:56 daemonizing the process 
2010-05-27T11:16:56 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:16:56 daemon manager started 
2010-05-27T11:16:56 spawned process pid=2171 
2010-05-27T11:16:56 (2171) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:16:56 (2171) opening storage '1' using FileStorage 
2010-05-27T11:16:56 (2171) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:16:56 (2171) listening on ('127.0.0.1', 8100) 
2010-05-27T11:21:42 (2171) terminated by SIGTERM 
2010-05-27T11:21:42 (2171) closing storage '1' 
2010-05-27T11:21:42 (2171) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:21:42 pid 2171: exit status 0 
2010-05-27T11:21:42 Exiting 
2010-05-27T11:21:43 daemonizing the process 
2010-05-27T11:21:43 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:21:43 daemon manager started 
2010-05-27T11:21:43 spawned process pid=2336 
2010-05-27T11:21:44 (2336) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:21:44 (2336) opening storage '1' using FileStorage 
2010-05-27T11:21:44 (2336) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:21:44 (2336) listening on ('127.0.0.1', 8100) 
2010-05-27T11:22:21 (2336) terminated by SIGTERM 
2010-05-27T11:22:21 (2336) closing storage '1' 
2010-05-27T11:22:21 (2336) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:22:21 pid 2336: exit status 0 
2010-05-27T11:22:21 Exiting 
2010-05-27T11:22:22 daemonizing the process 
2010-05-27T11:22:22 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:22:22 daemon manager started 
2010-05-27T11:22:22 spawned process pid=2349 
2010-05-27T11:22:22 (2349) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:22:22 (2349) opening storage '1' using FileStorage 
2010-05-27T11:22:22 (2349) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:22:22 (2349) listening on ('127.0.0.1', 8100) 
2010-05-27T11:22:43 (2349) terminated by SIGTERM 
2010-05-27T11:22:43 (2349) closing storage '1' 
2010-05-27T11:22:43 (2349) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:22:43 pid 2349: exit status 0 
2010-05-27T11:22:43 Exiting 
2010-05-27T11:22:50 daemonizing the process 
2010-05-27T11:22:50 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:22:50 daemon manager started 
2010-05-27T11:22:50 spawned process pid=2363 
2010-05-27T11:22:50 (2363) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:22:50 (2363) opening storage '1' using FileStorage 
2010-05-27T11:22:50 (2363) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:22:50 (2363) listening on ('127.0.0.1', 8100) 
2010-05-27T11:23:44 daemon manager killed by SIGTERM 
2010-05-27T11:23:44 (2363) terminated by SIGTERM 
2010-05-27T11:23:44 (2363) closing storage '1' 
2010-05-27T11:23:44 (2363) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:24:47 daemonizing the process 
2010-05-27T11:24:47 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:24:47 daemon manager started 
2010-05-27T11:24:47 spawned process pid=2116 
2010-05-27T11:24:47 (2116) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:24:47 (2116) opening storage '1' using FileStorage 
2010-05-27T11:24:48 (2116) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:24:48 (2116) listening on ('127.0.0.1', 8100) 
2010-05-27T11:27:52 (2116) terminated by SIGTERM 
2010-05-27T11:27:52 (2116) closing storage '1' 
2010-05-27T11:27:52 (2116) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:27:52 pid 2116: exit status 0 
2010-05-27T11:27:52 Exiting 
2010-05-27T11:27:52 daemonizing the process 
2010-05-27T11:27:52 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:27:52 daemon manager started 
2010-05-27T11:27:52 spawned process pid=2292 
2010-05-27T11:27:52 (2292) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:27:52 (2292) opening storage '1' using FileStorage 
2010-05-27T11:27:52 (2292) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:27:52 (2292) listening on ('127.0.0.1', 8100) 
2010-05-27T11:28:27 pid 2292: terminated by SIGKILL 
2010-05-27T11:28:27 spawned process pid=2299 
2010-05-27T11:28:27 (2299) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:28:27 (2299) opening storage '1' using FileStorage 
2010-05-27T11:28:27 (2299) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:28:27 (2299) listening on ('127.0.0.1', 8100) 
2010-05-27T11:28:32 (2299) terminated by SIGTERM 
2010-05-27T11:28:32 (2299) closing storage '1' 
2010-05-27T11:28:32 (2299) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:28:32 pid 2299: exit status 0 
2010-05-27T11:28:32 Exiting 
2010-05-27T11:28:32 daemonizing the process 
2010-05-27T11:28:32 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:28:32 daemon manager started 
2010-05-27T11:28:32 spawned process pid=2309 
2010-05-27T11:28:32 (2309) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:28:32 (2309) opening storage '1' using FileStorage 
2010-05-27T11:28:32 (2309) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:28:32 (2309) listening on ('127.0.0.1', 8100) 
2010-05-27T11:31:23 (2309) terminated by SIGTERM 
2010-05-27T11:31:23 (2309) closing storage '1' 
2010-05-27T11:31:23 (2309) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:31:23 pid 2309: exit status 0 
2010-05-27T11:31:23 Exiting 
2010-05-27T11:31:23 daemonizing the process 
2010-05-27T11:31:23 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:31:23 daemon manager started 
2010-05-27T11:31:23 spawned process pid=2330 
2010-05-27T11:31:23 (2330) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:31:23 (2330) opening storage '1' using FileStorage 
2010-05-27T11:31:23 (2330) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:31:23 (2330) listening on ('127.0.0.1', 8100) 
2010-05-27T11:55:57 (2330) terminated by SIGTERM 
2010-05-27T11:55:57 (2330) closing storage '1' 
2010-05-27T11:55:57 (2330) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:55:57 pid 2330: exit status 0 
2010-05-27T11:55:57 Exiting 
2010-05-27T11:55:57 daemonizing the process 
2010-05-27T11:55:57 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T11:55:57 daemon manager started 
2010-05-27T11:55:57 spawned process pid=2438 
2010-05-27T11:55:57 (2438) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T11:55:57 (2438) opening storage '1' using FileStorage 
2010-05-27T11:55:57 (2438) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T11:55:57 (2438) listening on ('127.0.0.1', 8100) 
2010-05-27T12:00:56 (2438) terminated by SIGTERM 
2010-05-27T12:00:56 (2438) closing storage '1' 
2010-05-27T12:00:56 (2438) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:00:56 pid 2438: exit status 0 
2010-05-27T12:00:56 Exiting 
2010-05-27T12:00:56 daemonizing the process 
2010-05-27T12:00:56 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T12:00:56 daemon manager started 
2010-05-27T12:00:56 spawned process pid=2474 
2010-05-27T12:00:56 (2474) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:00:56 (2474) opening storage '1' using FileStorage 
2010-05-27T12:00:56 (2474) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T12:00:56 (2474) listening on ('127.0.0.1', 8100) 
2010-05-27T12:05:32 (2474) terminated by SIGTERM 
2010-05-27T12:05:32 (2474) closing storage '1' 
2010-05-27T12:05:32 (2474) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:05:32 pid 2474: exit status 0 
2010-05-27T12:05:32 Exiting 
2010-05-27T12:05:32 daemonizing the process 
2010-05-27T12:05:32 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T12:05:32 daemon manager started 
2010-05-27T12:05:32 spawned process pid=2514 
2010-05-27T12:05:32 (2514) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:05:32 (2514) opening storage '1' using FileStorage 
2010-05-27T12:05:32 (2514) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T12:05:32 (2514) listening on ('127.0.0.1', 8100) 
2010-05-27T12:24:58 (2514) terminated by SIGTERM 
2010-05-27T12:24:58 (2514) closing storage '1' 
2010-05-27T12:24:58 (2514) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:24:58 pid 2514: exit status 0 
2010-05-27T12:24:58 Exiting 
2010-05-27T12:24:58 daemonizing the process 
2010-05-27T12:24:58 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T12:24:58 daemon manager started 
2010-05-27T12:24:58 spawned process pid=2709 
2010-05-27T12:24:58 (2709) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:24:58 (2709) opening storage '1' using FileStorage 
2010-05-27T12:24:58 (2709) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T12:24:58 (2709) listening on ('127.0.0.1', 8100) 
2010-05-27T12:41:16 (2709) terminated by SIGTERM 
2010-05-27T12:41:16 (2709) closing storage '1' 
2010-05-27T12:41:16 (2709) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:41:16 pid 2709: exit status 0 
2010-05-27T12:41:16 Exiting 
2010-05-27T12:41:19 daemonizing the process 
2010-05-27T12:41:19 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver' 
2010-05-27T12:41:19 daemon manager started 
2010-05-27T12:41:19 spawned process pid=2766 
2010-05-27T12:41:19 (2766) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid' 
2010-05-27T12:41:19 (2766) opening storage '1' using FileStorage 
2010-05-27T12:41:19 (2766) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs 
2010-05-27T12:41:19 (2766) listening on ('127.0.0.1', 8100)
```
I want to know how can I find out if there is a stale pid file what is that.Does strace helps to find that out?

---

### Post by StephenF on 2010-05-28
Every program running in your computer has a process ID, pid for short you can view them with the "ps -A" command in a console.

Pid files are generally used by programs that only want to have one instance running (such programs generally tie up a resource).

The mechanism is this: program launches, checks for a pid file if none is found it continues, otherwise it optionally signals the already running process (using the process ID found in the pid file), then it exits. When the incumbent instance exits it removes the pid file allowing the program to be launched again.

Where problems occur is when pid files are left lying around because the program did not exit normally. You can tell if a pid file is stale.

ps -A | grep `cat /path/to/pidfile`

If this prints nothing the pid is stale. If it prints a different application name to what you were expecting the pid file probably persisted beyond a reboot and is stale.

---

### Post by tapas_mishra on 2010-05-28
> **StephenF said:**
> 
Where problems occur is when pid files are left lying around because the program did not exit normally. You can tell if a pid file is stale.

ps -A | grep `cat /path/to/pidfile`

If this prints nothing the pid is stale. If it prints a different application name to what you were expecting the pid file probably persisted beyond a reboot and is stale.
But the point is how do you know /path/to/pid

---

### Post by soltanis on 2010-05-28
It depends on the application, although I've seen a few that use the directory /var/lock.

EDIT: And based on your code listing it's pretty obviously this file:

> 
2010-05-27T12:41:19 spawned process pid=2766 
2010-05-27T12:41:19 (2766) created PID file '**/opt/eduCommons-3.2.1/var/zeoserver.pid**' 

---

### Post by tapas_mishra on 2010-05-28
> **soltanis said:**
> It depends on the application, although I've seen a few that use the directory /var/lock.

EDIT: And based on your code listing it's pretty obviously this file:

Yah you pointed the right thing.But just imagine when I did not knew this thing I was not having any clue.I was more than lucky that some one helped me but this may not be a usual case.
I am wondering if there is  some tool which can debug Linux or bring it back to previous state or may be it can tell which files or processes had changed between 2 time intervals .I am just giving an idea do not know how to put it in words.As how can we manage the debugging ourselves.Stale pid is just one simple case do not know how many more I will be facing.

---

### Post by soltanis on 2010-05-29
There is a tool called strace which is very flexible. It gives detailed information on all the system calls a program makes, and thus is an invaluable debugging tool.

I would get it, read it's manpage, and experiment with it a little. It is quire powerful.

---

### Post by tapas_mishra on 2010-05-29
Yes I had read about that some where.Can you give some link based on your experience which you may have referred.

---

