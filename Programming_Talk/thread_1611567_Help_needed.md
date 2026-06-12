---
title: "Help needed"
date: 2010-11-02
forum: Programming Talk
---

### Post by mak753 on 2010-11-02
Can any1 help me to make a mini project.

1. Create two processes which communicate using a shared memory segment. The
first process finds out the list of all processes running on the system with their
name, process id, number of files opened and total time running and creates a
linked list containing this data about every process running in the shared memory.
The second process reads this linked list and formats it in HTML and saves it in a
file. This is done by the processes every half an hour. 

2.Take the same server which was developed in (1) and change the client as
described. The goal of the client this time is to find out the processes which are
executing continuously in the running state over a period of 5 minutes. For this
the server also sends the state of the running processes at the time the snapshot
was taken. The server takes the snapshot repeatedly over 5 minutes and writes the
linked list in the shared memory as soon as the client is done with the previous
linked list. The client keeps a count for each process of the -number of times the
process was in the running state. At the end of 5 minutes the client prints out the
list of processes running in descending order of the counts recorded by the client

---

### Post by Some Penguin on 2010-11-02
Sure.  Start with

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)
and
[http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)

---

