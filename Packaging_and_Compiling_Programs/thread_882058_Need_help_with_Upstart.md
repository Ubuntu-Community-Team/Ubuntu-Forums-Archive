---
title: "Need help with Upstart"
date: 2008-08-06
forum: Packaging and Compiling Programs
---

### Post by gscott2112 on 2008-08-06
I need a little help understanding the Upstart process.

I have a program that I want to run as a service and I'm trying to use Upstart to handle it.

I have a job file that can start and stop the service, the problem is that the start command never returns me to the shell and I need to interupt the process to get my shell back.

>sudo start myjob

never terminates.

From what I read my program does not need to daemonize itself when using upstart.  When I modify my jobfile to supply the daemon flag to my app or simply launch in the background with &, the 'start myjob' command will return and my app is running, but the subsequent 'stop myjob' results in an error

stop: Job not changed: myjob

Here is my job file,  what am I missing here?

myjob:

start on startup
start on runlevel 2
start on runlevel 3
start on stopped rcS

exec /usr/local/myapp/mytestapp

---

