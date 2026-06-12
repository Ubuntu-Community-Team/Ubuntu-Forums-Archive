---
title: "'exit' shell script does not terminate child process"
date: 2009-11-19
forum: Programming Talk
---

### Post by makaveli789 on 2009-11-19
I have a shell scripting question. More of a strange issue that I need help understanding, actually.

I have a shell script that looks like this:
```

#!/bin/bash

gedit testfile &
for i in {5..1}
do
   echo $i
   sleep 1
done
exit 0

```What I expect happen when I launch this script is for it to open up gedit and then countdown from 5 to 1, then exit whilst bringing down gedit along with it. What actually happens is that gedit remains open (and visible). Similarly, if I run this from the the command line in Gnome Terminal:

```
gedit testfile &
```and then type exit, the gedit window remains open. However, if instead of typing exit in the terminal, I simply close it by clicking the X on the window. The gedit window closes and the process terminates.

I am totally baffled as to what is going on here. If Somebody could at least explain the difference of typing exit and shutting the terminal down then that would be awesome. On a side note, this is a test that I am performing to see if child processes will close when you terminate a shell script.

---

### Post by Arndt on 2009-11-19
> **makaveli789 said:**
> I have a shell scripting question. More of a strange issue that I need help understanding, actually.

I have a shell script that looks like this:
```

#!/bin/bash

gedit testfile &
for i in {5..1}
do
   echo $i
   sleep 1
done
exit 0

```What I expect happen when I launch this script is for it to open up gedit and then countdown from 5 to 1, then exit whilst bringing down gedit along with it. What actually happens is that gedit remains open (and visible). Similarly, if I run this from the the command line in Gnome Terminal:

```
gedit testfile &
```and then type exit, the gedit window remains open. However, if instead of typing exit in the terminal, I simply close it by clicking the X on the window. The gedit window closes and the process terminates.

I am totally baffled as to what is going on here. If Somebody could at least explain the difference of typing exit and shutting the terminal down then that would be awesome. On a side note, this is a test that I am performing to see if child processes will close when you terminate a shell script.

What probably happens when you click the X is that the process managing the window (gnome-terminal) decides it should close things down, and sends a suitable signal (maybe SIGTERM) to the process group of the shell process which it created. All processes spawned by that shell belong to that process group (unless they explicitly start a new process group), so then they all are terminated.

When you do 'exit' in a shell, no signal is sent anywhere.

---

### Post by makaveli789 on 2009-11-20
> **Arndt said:**
> What probably happens when you click the X is that the process managing the window (gnome-terminal) decides it should close things down, and sends a suitable signal (maybe SIGTERM) to the process group of the shell process which it created. All processes spawned by that shell belong to that process group (unless they explicitly start a new process group), so then they all are terminated.

When you do 'exit' in a shell, no signal is sent anywhere.

Thanks for that Arndt. It does make sense. But why would the exit command not cause a similar signal to be issued. I used to think that closing a terminal from the gui and from the exit command were the exact same thing.

---

### Post by Arndt on 2009-11-20
> **makaveli789 said:**
> Thanks for that Arndt. It does make sense. But why would the exit command not cause a similar signal to be issued. I used to think that closing a terminal from the gui and from the exit command were the exact same thing.

There is a system call to cause a process to stop. It's called _exit. To make the shell stop, a command was implemented which uses this system call, and it too was named "exit". That's all.

---

### Post by makaveli789 on 2009-11-20
Yeah, I came across this _exit command this morning. I found that I couldn't use it in my bash script as the command was not found. Does this _exit command relate to a specific shell??

---

### Post by Arndt on 2009-11-20
> **makaveli789 said:**
> Yeah, I came across this _exit command this morning. I found that I couldn't use it in my bash script as the command was not found. Does this _exit command relate to a specific shell??

How did you come across it? You only see it when programming in C, I guess. Do "man 2 exit". Normally, a program doesn't want to use the raw _exit directly - it wants to flush buffers and such things first, which is why the usual exiting function in C is 'exit', not '_exit'.

---

### Post by makaveli789 on 2009-11-20
> **Arndt said:**
> How did you come across it? You only see it when programming in C, I guess. Do "man 2 exit". Normally, a program doesn't want to use the raw _exit directly - it wants to flush buffers and such things first, which is why the usual exiting function in C is 'exit', not '_exit'.
I was reading this webpage: [URL="http://www.unixguide.net/unix/programming/1.1.3.shtml"]http://www.unixguide.net/unix/programming/1.1.3.shtml
[/URL] 
```
user@ubuntu-desktop:~$ man 2 exit
No manual entry for exit in section 2
```As I sidenote the same website has this: [Why doesn't my process get SIGHUP when its parent dies?]("http://www.unixguide.net/unix/programming/1.15.shtml")
> ...as part of the session management system, there are exactly two 
cases where SIGHUP is sent on the death of a process: 

[LIST]
[*] When the process that dies is the session leader of a session that is 
attached to a terminal device, SIGHUP is sent to all processes in 
the foreground process group of that terminal device.
[*] When the death of a process causes a process group to become orphaned, 
and one or more processes in the orphaned group are *stopped*, then 
SIGHUP and SIGCONT are sent to all members of the orphaned 
group.  (An orphaned process group is one where no process in the group 
has a parent which is part of the same session, but not the same process 
group.)
[/LIST]


---

### Post by Arndt on 2009-11-20
> **makaveli789 said:**
> 

```
user@ubuntu-desktop:~$ man 2 exit
No manual entry for exit in section 2
```



You need to install manpages-dev, I think.

---

### Post by makaveli789 on 2009-11-23
From reading around I've gained a better understanding of this bash exit issue. And I've come to the conclusion that this is normal behaviour - and what is happening is as you described in your first reply.

Thanks for your help on this, Arndt. ;)

---

