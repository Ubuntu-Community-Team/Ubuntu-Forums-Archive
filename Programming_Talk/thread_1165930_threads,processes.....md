---
title: "threads,processes...."
date: 2009-05-21
forum: Programming Talk
---

### Post by touka12 on 2009-05-21
:KS

Hi, everyone,
I am sorry but i didn't found a better catgory for my questions other than this one :)
my questions are about OS, threads and processes,
I have an exam dealing with that, and i have to answer "yes" "no" or "other" to some questions
1/ each process creates his own threads : i think the answer to this question is "other" because , yes a process creates his own threads ,but if we use "fork", the threads of the father process will be duplicated to his child, isn't it ?

2/ a process doesn't contain any threads before we creat them : i think it is a "no" because of the father-child matter ? 

3/ all the threads of a process receives and treat the signals SIGINT received ? (i don't now how to answer this one)
4/when sending SIGINT to a process, that won't kill him : my answer is "no" cause SIGINT kill the process 
5/the child process runs always before the father process : don't know how to answer to this one !!!
and finally
6/ Ctrl-C send a SIGINT simultaniously to the child process and his father (don't know how to answer this )

thanks anyway :D

---

### Post by stroyan on 2009-05-21
You really need to be clear about which threading specification you are working with.  The implementations of threading vary between different operating systems and different releases of them.
The most common threading specification is the POSIX one.
You can review that at [http://www.unix.org/single_unix_specification/](http://www.unix.org/single_unix_specification/)
But almost all implementations diverge from that in some way.

---

### Post by Rocket2DMn on 2009-05-21
Sorry, we don't do homework help here.  Thread closed.

---

