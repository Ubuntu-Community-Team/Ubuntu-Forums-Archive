---
title: "Daemon_Module_SystemCall ??"
date: 2012-05-24
forum: Programming Talk
---

### Post by LunixVictim on 2012-05-24
I have homework =)

Aim of this project is implementing a system call in the Linux Kernel. 
I am asked to implement a new system call to output the process information into /var/log
directory. I will create my own logging daemon and my user space program will cause a call
in this daemon. 
my project consist of three basic parts:
1. Kernel System call
2. Logging daemon
3. User Space program
I will create a new system call in the Linux Kernel with my name (e.g. Ahmet) and this
new system call will get information about the current running process. I are asked to dump the
below information:
1. Process ID
2. Process name 
3. Owner of the process
4. Running Time of the Process
5. Memory Usage
6. CPU Usage
Also my kernel module will pass those information to a daemon waiting on the background. The
daemon will dump the information into a log file below /var directory. 
Finally, I will test the running scenario by calling the kernel module I have implemented by a
user space C program . 
Soo I need help :)
I dk how &#305; can write daemon .
Can you show me any exp. about this project.
Or explain step by step plzz

---

### Post by LunixVictim on 2012-05-24
example for daemon :
[http://www.enderunix.org/docs/eng/daemon.php](http://www.enderunix.org/docs/eng/daemon.php)

example for linux module :
[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN128](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN128)

example for system call :
[http://stackoverflow.com/questions/2103315/linux-kernel-system-call-hooking-example](http://stackoverflow.com/questions/2103315/linux-kernel-system-call-hooking-example)

but thats not enough forme :(

---

### Post by LunixVictim on 2012-05-25
[CENTER]Hope this picture helps to u
[[img]http://c1205.hizliresim.com/x/t/6qfds.png[/img]](http://bit.ly/c25MCx)[/CENTER]

---

