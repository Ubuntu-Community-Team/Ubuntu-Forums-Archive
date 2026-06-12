---
title: "User mode to Kernel mode"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by climb.colorado on 2008-06-25
Hey!

Can anyone tell me what the three styles of switching are in regards to switching from user mode to supervisor mode?  I've heard many different things but want to get a more qualified consensus. Thanks to everyone!

---

### Post by Cypher on 2008-06-25
Switching what? Context and more details please..are we talking drivers?

---

### Post by climb.colorado on 2008-06-25
This is just a question in regards to the technical aspects of my operating system.  "What are the 3 styles of switching from users mode to supervisor (or Kernel) mode?"I guess I have no more information than that. Sorry...

---

### Post by ukripper on 2008-06-25
> **climb.colorado said:**
> This is just a question in regards to the technical aspects of my operating system.  "What are the 3 styles of switching from users mode to supervisor (or Kernel) mode?"I guess I have no more information than that. Sorry...

This will help you understand basic aspects of Ubuntu 8.04

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cypher on 2008-06-25
OK..how about putting it another way, where are you getting that particular question from? A book, a website? 

Why do you think there are 3 styles exactly? The context of your question will greatly determine the answer.

For majority of users of Linux, everything you do is usually in user space, your applications, desktop, videos, music, etc. You will use SUDO/GKSU/KDESU to perform administrative tasks, but that is still within "user" space. 

You don't enter Kernel space unless you are talking specifically about a driver that is either loaded using INSMOD/MODPROBE or built right into the Kernel.

All data between the Kernel and User space that are handled by a driver are translated to cross that boundary safely.

Hope that explains a little..

---

