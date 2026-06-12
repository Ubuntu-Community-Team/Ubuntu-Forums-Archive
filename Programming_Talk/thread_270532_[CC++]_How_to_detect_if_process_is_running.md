---
title: "[C/C++] How to detect if process is running?"
date: 2006-10-03
forum: Programming Talk
---

### Post by Laterix on 2006-10-03
I would need to know if process is running and then execute actions based on that. For example if banshee is running -> pause banshee. 

I know I can run *PS -A | grep banshee* and this returns 0 or 1 lines. But how can I get *ps* command output into my program? Or is there some better way to access processtable directly?

---

### Post by linux2512 on 2006-10-03
You can iterate through the process folders in /proc looking at the 'status' file.

---

### Post by Laterix on 2006-10-03
> **linux2512 said:**
> You can iterate through the process folders in /proc looking at the 'status' file.
Yeah, I thought this one, but it feels slow way to do it. It's important to me that this detecting is as fast as possible.

And also is it even possible to get some program's output text into my own program? Well... sure somehow, but what is the right way to do that?

---

### Post by linux2512 on 2006-10-03
Well I don't think iterating through the /proc filesystem is slow, I think the ps command does the same thing.  But to save coding time then I guess you could create a FIFO using mkfifo, have your app attach to the FIFO and redirect the output from the ps command to the FIFO.

There are many other ways to accomplish IPC, that's just one that pops into my head.

Hope this helps.

---

### Post by Roptaty on 2006-10-03
> **Laterix said:**
> Yeah, I thought this one, but it feels slow way to do it. It's important to me that this detecting is as fast as possible.



Remember that spawning another process is a time consuming process. I believe that iterating through the /proc file system is much faster than spawning a process which use the /proc system as well...  


> 
And also is it even possible to get some program's output text into my own program? Well... sure somehow, but what is the right way to do that?

Yes, this is possible. You can for instance read [this](http://www.linuxhq.com/guides/LPG/node11.html).

---

### Post by Laterix on 2006-10-03
Thanks for the help. I'll take a look of those pipes. And that's true that spawning a new process is a slow operation to do. Maybe I'll just iterate /proc then.

---

### Post by Arndt on 2006-10-05
> **Laterix said:**
> I would need to know if process is running and then execute actions based on that. For example if banshee is running -> pause banshee. 



A much used convention for daemons is that they store their pid in a suitably named file in /var/run. For example, /var/run/sshd.pid. So to see if sshd is running, you can open that file, read the pid, do a kill(pid,0) in the language of choice and see what is returned.
Maybe your daemons use this file too.

---

