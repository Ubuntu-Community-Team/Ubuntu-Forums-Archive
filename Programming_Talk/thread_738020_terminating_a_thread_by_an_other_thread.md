---
title: "terminating a thread by an other thread"
date: 2008-03-28
forum: Programming Talk
---

### Post by seleciii44 on 2008-03-28
hi. I am writing a multi-threaded program. One of the threads must be terminated from an other thread and i don't know how to do! Waiting for your help!
thanks...

---

### Post by pedro_orange on 2008-03-28
Theoretically, you can kill a thread as long as you know it's thread ID. 

If you're using pthreds: [http://www.opengroup.org/onlinepubs/007908775/xsh/pthread_cancel.html](http://www.opengroup.org/onlinepubs/007908775/xsh/pthread_cancel.html)

---

### Post by seleciii44 on 2008-03-28
i hate linux but i love its forums:lolflag:
thanks a lot

---

### Post by seleciii44 on 2008-03-28
:) but now, I have a new problem. I realize that, I have to terminate thread and PROCESS. &#305;f &#305; know this process fork id, how can I terminate this process.
please help me again :)

Note : Actually, I love linux :D

---

### Post by pedro_orange on 2008-03-28
I don't know how to do that programmatically. I guess you will have to research for the relevant system call, and how it is used within your language of choice.

But I know you can kill a process using the following shell command:

```
kill -9 Process_ID
```

You can invoke that from C using system()

---

### Post by imdano on 2008-03-28
You could probably just send it a SIGTERM signal if it's a child process.  Not sure how to do this in C but I'm sure there's a way.

---

### Post by themusicwave on 2008-03-28
Just for clarification, did you write the Thread and Process?

If so why not just add some code to them to control them?  Then the master program can just tell them to stop as needed.  This is generally much better than calling abort or kill or whatever on them.

Usually when I do threaded programming I do something like this:

Thread Class:
```

threadMethod()
   While run
         Do stuff

    do some cleanup here

setRun(r)
      run = r


```

The the master can just call setRun(false) to stop the child thread.  You can also add some nice graceful shutdown to this method.  

You always want to try to kill things nicely so they don't make a mess  when they die.

Knowing more information like the language you are using would help.

Also, why are you killing your own threads and processes?  Is this for when they enter a crashed state of something?

---

### Post by stroyan on 2008-03-28
You can send a signal to a process from C with "kill(pid,signum)".
With linux and glibc you can use "tkill(tid, signum)" to send a signal to a thread.
See "man 2 kill" to  read the manual for the library call instead of the command.
It is dangerous to cancel or kill a thread as resources like locks may not be
released well with an abrupt termination.  On the other hand, polling a variable
like "while (run)" can waste CPU time by not blocking a thread or result in slow
response because the variable is not checked very often.

---

### Post by LaRoza on 2008-03-28
Great, I thought it was something I could help with.

(Closing threads is easy)

---

### Post by heikaman on 2008-03-28
> **stroyan said:**
> It is dangerous to cancel or kill a thread as resources like locks may not be
released well with an abrupt termination.

Actually you can register a cleanup function “called cleanup handlers”  that gets called  do the cleanup when the thread exits or is canceled, for example, to release a lock, free memory allocated with malloc or whatever u want to do.
To register/unregister a cleanup handler call pthread_cleanup_push/ pthread_cleanup_pop from within the thread you want to register the cleanup handler to. 
see man  pthread_cleanup_push for args and info.

---

### Post by seleciii44 on 2008-03-29
Thanks you all for your concerns. Sending a signal may be a good idea but i have to try it now. I hope it runs.

---

