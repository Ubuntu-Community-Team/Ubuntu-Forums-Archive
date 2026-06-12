---
title: "network programming in c/c++"
date: 2011-02-09
forum: Programming Talk
---

### Post by trasheddesk on 2011-02-09
Hi,

I would like to know what are the good books available in the market for network programming c/c++ (preferably c++). I know the book by Richard Stevens (UNIX Network Programming) is very popular, I tried using it. The problem I experienced using that book is source code provided itself needs to modified to get them working. What I need is a book in which the source code works and then I can tinker with the code to learn. 

Any pointers in this regard is appreciated.  

Thanks.

---

### Post by trasheddesk on 2011-02-09
> **aspetg said:**
> I personally use "The Waite Group's Object-Oriented Programming in C++".  check it out..

Thanks for the reply, but doesn't this book teach only C++. I wanted to know books dealing with network programming (or socket programming if you prefer). I can program in C/C++, but I have little experience with TCP/IP networks and network programming. 
So please let me know if there are any good books for this.

Thanks.

---

### Post by worksofcraft on 2011-02-09
> **trasheddesk said:**
> Thanks for the reply, but doesn't this book teach only C++. I wanted to know books dealing with network programming (or socket programming if you prefer). I can program in C/C++, but I have little experience with TCP/IP networks and network programming. 
So please let me know if there are any good books for this.

Thanks.

An awfully long time ago I used [Internet Programming By Kris Jamsa and Ken Cope]("http://www.amazon.com/Internet-Programming-Book-Disk-Jamsa/dp/1884133126") I thought it was very good at the time but it is geart to Microsoft Winsock and probably very out of date by now.

---

### Post by axiomatic on 2011-02-10
I'd give boost asio a shot. Unfortunately it's not that well documented. However the upsides would be 
 - a pure-ish c++ api 
 - might make it into the standard or at least become the reference implementation
 - portable

As I said the documentation is lacking so mostly you'll have to learn from the examples provided and/or browsing the implementation but I got the impression that that is what you want anyway.

---

