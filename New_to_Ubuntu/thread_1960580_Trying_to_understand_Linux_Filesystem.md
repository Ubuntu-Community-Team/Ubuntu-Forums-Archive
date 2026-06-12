---
title: "Trying to understand Linux Filesystem"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-04-17
I came from windows and OS X. In OS X there is an applications folder and in windows I can see my program files under the C drive. But when I go look for something similar in Linux I am lost. I tried googling some stuff but nothing helpful came up. Can anyone here provide assistance?

---

### Post by Cheesemill on 2012-04-17
A bit of light reading for you :)

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)
[http://www.tuxradar.com/content/take-linux-filesystem-tour](http://www.tuxradar.com/content/take-linux-filesystem-tour)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by anewguy on 2012-04-17
There is no 1 such folder.  Things get installed in different folders from the same package.  Some things get installed in the /usr folders, others elsewhere.  It just depends on the app.

So, if you are trying to look at a single folder and say "this is what is installed on my system" you won't be able to do so.

If you are looking for something specific, post back and we can go from there.

Welcome to Ubuntu!

Dave ;)

---

### Post by enkay009 on 2012-04-17
It can be tricky if your coming from Windows. But if your coming from OSX it shouldn't be too much of a curve... assuming you spent time in the terminal.

What you're referring to is the file system hierarchy. 

Take a look at the below link. It gives you a nice overview of how most Linuxes organize their file system.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Normally however, I don't browse the file system past my home directory. I make calls to commands located outside of it. But I have to admit, when I started using Linux I did have the same itch you do.

---

### Post by TheMTtakeover on 2012-04-17
> **Cheesemill said:**
> A bit of light reading for you :)

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)
[http://www.tuxradar.com/content/take-linux-filesystem-tour](http://www.tuxradar.com/content/take-linux-filesystem-tour)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
Thanks that top one is an extremely useful break down.

> **anewguy said:**
> There is no 1 such folder.  Things get installed  in different folders from the same package.  Some things get installed  in the /usr folders, others elsewhere.  It just depends on the app.

So, if you are trying to look at a single folder and say "this is what is installed on my system" you won't be able to do so.

Dave :wink:
BLAH! That's what I was looking for. Not looking for anything specific just getting to know my way around. 

Thanks for the help guys

---

### Post by TheMTtakeover on 2012-04-17
> **enkay009 said:**
> It can be tricky if your coming from Windows. But if your coming from OSX it shouldn't be too much of a curve... assuming you spent time in the terminal.

What you're referring to is the file system hierarchy. 

Take a look at the below link. It gives you a nice overview of how most Linuxes organize their file system.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

Normally however, I don't browse the file system past my home directory. I make calls to commands located outside of it. But I have to admit, when I started using Linux I didn't have the same itch you do.

Only ever did one or two things in the terminal. Thanks for the link and Help though

---

