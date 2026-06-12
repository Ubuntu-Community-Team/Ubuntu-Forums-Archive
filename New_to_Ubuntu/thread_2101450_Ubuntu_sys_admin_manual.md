---
title: "Ubuntu sys admin manual"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by venkinag on 2013-01-04
Hi, I am a windows user(for quite sometime) and I have recently installed Ubuntu 12.10.  But I have fairly good knowledge about SCO unix.  

Please someone point me to ubuntu 12.10 sys admin manual?

My aim is to understand

* How the filesystem is organised (i.e., system files, program files etc)?

* How the process are organised (i.e., init, cron etc)

* Where the individual user profiles are stored and how to configure them?

* How to make a program available to all users and/or how to prevent a program accessible by all users?

Thanks.

---

### Post by DuckHook on 2013-01-04
AFAIK there's no sysadmin "manual". Linux is far too big and disparate to be contained in a manual. Please be aware that, unlike Windows or even SCO UNIX, Linux is a community effort. I always liken it to the world's largest and most complicated community garden. You'll find a lot of gardeners (read: gurus) who have been doing it for a long time and have become a world authority on, say, potatoes, and you'll find some who know about pest resistance like it's nobody's business, but I don't know of anyone who knows the whole thing. Even the high priests like Linus Torvalds and RMS don't know everything--it's grown so far beyond what they started.

Generally, I find that there are three ways to learn Linux:

1. The highly structured way (reading books, taking courses, etc). A good place to start is [here]("http://www.linuxtopia.org/online_books/linux_administration_index.html") and [here]("https://training.linuxfoundation.org/"). 
2. The less structured way (the man pages, separate guides, howtos, etc.) A good place for that is [here]("http://ubuntuforums.org/showthread.php?t=1046738").
3. The hippy way (cruising forums, asking questions, picking up bits and pieces). Can't point you to any specific resources (other than this forum) because it's mostly a process of osmosis.

It depends on your learning style. I subscribe to a combination of 2 and 3. But then, I'm retired and have the time to treat it as a hobby.

---

### Post by haqking on 2013-01-04
> **venkinag said:**
> Hi, I am a windows user(for quite sometime) and I have recently installed Ubuntu 12.10.  But I have fairly good knowledge about SCO unix.  

Please someone point me to ubuntu 12.10 sys admin manual?

My aim is to understand

* How the filesystem is organised (i.e., system files, program files etc)?

* How the process are organised (i.e., init, cron etc)

* Where the individual user profiles are stored and how to configure them?

* How to make a program available to all users and/or how to prevent a program accessible by all users?

Thanks.

[http://aplawrence.com/Linux/scolindiff.html](http://aplawrence.com/Linux/scolindiff.html)

---

### Post by redmk2 on 2013-01-04
> **venkinag said:**
> Hi, I am a windows user(for quite sometime) and I have recently installed Ubuntu 12.10.  But I have fairly good knowledge about SCO unix.  

Please someone point me to ubuntu 12.10 sys admin manual?

As @DuckHook has pointed out there is no centralized manual of "Linux".  The various projects that make up a particular distro (i.e. Ubuntu, Debian, Fedora, Arch) should have documentation.  For Ubuntu you might try [**[COLOR="Blue"]here[/COLOR]**]("https://help.ubuntu.com/").  It really helps to learn how to search on the various subjects (key words) for information.  > 

My aim is to understand

* How the filesystem is organised (i.e., system files, program files etc)?
Search on *[**_[COLOR="Blue"]Linux File System Hierarchy[/COLOR]_**]("linux filesystem hierarchy")*> 

* How the process are organised (i.e., init, cron etc)
Start with the  the various man (manual pages) This will give you some idea on what to search for.```
man cron

man init
```
 > 

* Where the individual user profiles are stored and how to configure them?

In the users home directory.  They are hidden files (preceded with a dot (.) ) > 

* How to make a program available to all users and/or how to prevent a program accessible by all users?
The traditional way is with file permissions.  See ```
man chmod
man chown
```

It will help for you to learn the basic commands available at the CLI.  See [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=basic+linux+commands&btnG=Go!").

Again @DuckHook is right.  No one ever learns everything in Linux.  Pick the parts that you are interested in and start your Google searching.  Good Luck!

---

### Post by ibjsb4 on 2013-01-04
Here's a few more.

[http://ubuntuguide.org/wiki/Ubuntu_Precise_System_Administration](http://ubuntuguide.org/wiki/Ubuntu_Precise_System_Administration)

[https://help.ubuntu.com/community/SystemAdministration](https://help.ubuntu.com/community/SystemAdministration)

[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

