---
title: "check if process is still running?"
date: 2009-03-11
forum: Programming Talk
---

### Post by any.linux12 on 2009-03-11
Hi!

How can I see if one process that I started in my script is still running?
like after I have the number do something like an if to see if it is "alive"

Please help
and thnks

---

### Post by stumbleUpon on 2009-03-11
ps -ef | grep processName

---

### Post by any.linux12 on 2009-03-11
> **stumbleUpon said:**
> ps -ef | grep processName

What? like, I have the process number. I just want to see if it is working.
I don't know much about unix script so can you tell me how can I do an if with that??

---

### Post by stumbleUpon on 2009-03-11
What do you mean by saying if you want to see if the process is working?

If you have the process number, just do 'top' in a terminal and see if that process is running. You cant get an idea if the process is running properly from here.

---

### Post by any.linux12 on 2009-03-11
but I want do a script that:

First: executes a svn command and stores the process number in a var
Second: executes a zinity command, which in my case is a process bar
Third: checks with an if, if the svn command is done (or if you prefer not running) and kills the zinity bar.

thanks

---

### Post by stumbleUpon on 2009-03-11
this is from here

[http://help.lockergnome.com/linux/test-process-running--ftopict398766.html](http://help.lockergnome.com/linux/test-process-running--ftopict398766.html)

if you know the process id, then check if a directory with that id exits in /proc/

easily done in python

if os.path.exists("/proc/"+processID):

or else in a shell script

DIR=/proc/processID
if [-d $DIR]

---

