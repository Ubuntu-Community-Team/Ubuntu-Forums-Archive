---
title: "Terminating a misbehaving Python script?"
date: 2010-08-27
forum: Programming Talk
---

### Post by SRabin on 2010-08-27
I've searched around and every result for 'bash kill process' or 'bash terminate process' involves executing more commands from bash - unfortunately, when my script throws an error I'm not catching, I can't execute any commands from that terminal. Closing the terminal obviously kills the process, and it was my understanding that Ctrl+C terminates the process, but that doesn't seem to work. I've seen references to 'trap "kill 0" 2', but that's for bash and I'm not sure how to incorporate something similar into a Python script.

Any suggestions? I'm deliberately not catching the exceptions so the program crashes out immediately after encountering an error so I can address them as I find them. I'm only now starting to learn Python and this is a learning exercise.

---

### Post by Martin Witte on 2010-08-27
You could start with catching the root of all exceptions, like
```
martin@martinspc:~$ cat test.py
#!/usr/bin/env python

try:
	raise StandardError("test")
except Exception as inst:
	print type(inst)
	print inst
martin@martinspc:~$ ./test.py
<type 'exceptions.StandardError'>
test
martin@martinspc:~$ 

``` 
That gives you more information and control than a crash, make sure you inherit exceptions you create yourself from Exception. For more advice please post an if possible minimal examle of your code which demonstrates your issue

---

### Post by SRabin on 2010-08-27
This script uses the QtWebKit library, and looking at your test.py script made me realize that by not catching the root error, I was never calling app.exit(), and the QApplication was never quitting. I've wrapped the call to make sure the QApplication exit()s and the problem is gone. Amazing what a little reminder that you're not doing it right can do to job your memory!

Is there a way to get the executing script to terminate regardless, without altering the Python script? I don't know enough about the QtWebKit library and I'll ask this question there too; not sure what's happening under the hood and how to get the running app to quit if the script errors out.

---

### Post by MadCow108 on 2010-08-27
get the process id (PID), e.g. with *pgrep process-name* or *ps x*
and type *kill process-id*
if that does not work use *kill -9 processid*
this works from any shell
if you are in the same shell where the process was started you can also use the jobnumber (retrieved by jobs command):
kill %jobnumber

if you know the process name *killall name* is another possibility (assuming you really want to kill all processes with that name)

stopping of processes is done over signals, see
man kill
for details

the important ones for this subject are interrupt, terminate and kill.
Interrupt (= ctrl +c in most terminals) usually asks the process to end gracefully. But the process does not have to respect that convention (or it is to broken to handle the signal)

then you have to open another shell and send the terminate signal to it (with kill).
This will usually stop the process.
In some cases not even terminate works and you have to send the kill signal (kill -9)
this should work in almost all cases.

From my experience sometimes when ctrl + c does not work ctrl + z still works.
This is usually bound to the suspend signal which halts a process (resume with fg)
and you get the processid and jobnumber displayed
then you can kill it in the same shell with kill %+ which kills the last job
(kill pid of course also works)

another hint: even when your x server is broken you can mostly still get a shell to kill or restart processes with the ctrl + alt + f1-6 keystrokes.
ctrl + alt +f7 usually gets you back to the shell with X

---

