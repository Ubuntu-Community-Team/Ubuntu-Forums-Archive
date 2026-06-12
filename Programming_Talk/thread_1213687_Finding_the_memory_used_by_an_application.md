---
title: "Finding the memory used by an application"
date: 2009-07-15
forum: Programming Talk
---

### Post by codingfreak on 2009-07-15
Hi

Is there any tool or procedure where I can find the overhead in running my application i.e. a.out.

My application might be using system calls transferring data from Kernel space to user space vice versa and many other operations. Is there way where I can find out if I run my application continuously what would be the memory usage, processor usage and so on.

---

### Post by MindSz on 2009-07-15
I believe there's a way to do it inside your program, but I can't remember what it is right now.

However, if you type 'ps aux' in your terminal you should be able to see all the applications currently running on your system. To see only the application you're interested in, use grep.

e.g. 'ps aux | grep a.out'

---

### Post by drs305 on 2009-07-15
You can type "top" in a terminal. One with a bit of improvements is "htop", which you would have to install.

---

### Post by Zugzwang on 2009-07-15
For the record: You might add some "getchar()" command before the exit procedure of your application such that you know when it's done. Then you can have a look at "/proc/<PID>/status". The "VmPeak" line might be the one you want.

---

### Post by codingfreak on 2009-07-15
I think ps and top commands are helpful in deciding the overall memory usage in percentages or MB's they might not be real time [Correct me if I am wrong].

What I want exactly is when a process or an executable is running then how can I find its realtime byte by byte memory status ... if possible even memory leaks ....

My application is a Network Sniffer. So it sniffs packets from Network in promiscous mode. When a packet is captured it should be transfered from kernel space to user space. So I want to know in real time the overhead my application creates if there is a huge data transfer.

---

