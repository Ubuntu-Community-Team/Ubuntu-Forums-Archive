---
title: "IcePodder on Ubuntu 8.04?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Gyrotwister on 2008-05-18
Is there a way to install IcePodder onto Ubuntu 8.04?  

When I try to install I get "Error: Dependency is not satisfiable: python-xmms".

---

### Post by shifty_powers on 2008-05-18
search for it in

packages.ubuntu.com/

or look at

[http://packages.debian.org/python-xmms](http://packages.debian.org/python-xmms)

which should work as well ;)

---

### Post by Gyrotwister on 2008-05-18
Is that link supposed to take me somewhere?  

Could you be more explicit?

---

### Post by shifty_powers on 2008-05-18
heh the first one, (need to copy and paste it into your adress bar), is the official ubuntu repositories, where they store all the programs you can download in synaptic/apt. If you go to the page, and search for python-xmms, it will let you download the .deb package and tell you what the dependencies are.

(deb packages are like exe packages iwindows. just double click it and let gdebi install it for you ;)).

The second link is one to the same but for debian, which is what ubuntu is based on. (Hence using .deb packages ;)). I know for a fact that python-xmms is there, and usually, most debain packages will work on ubuntu ;)

---

### Post by bsmith1051 on 2008-05-19
the 'current' version of IcePodder simply isn't compatible with Ubuntu 8.04!  Instead, you need to do a slightly more complicated procedure to download and configure the rewritten version (it has the same features but fewer dependencies).

First, open a command-prompt and run these commands:
```
 > sudo apt-get install subversion
 > svn co https://icepodder.svn.sourceforge.net/svnroot/icepodder icepodder
 > cd icepodder
 > sudo ./install.sh 
```

Next, go into System > Administration > Synaptic, and install "python-wxversion"

You now have a working copy of the 'wx' version of IcePodder!  You'll need to create a shortcut for it, i.e., /usr/bin/iPodder (note the upper-case 'P' because the command *IS* case sensitive)

---

### Post by bogaerbr on 2008-05-20
Thanks a lot.
This worked as a charm.


bruno

---

### Post by Gyrotwister on 2008-05-21
Somewhat buggy on my machine.  Won't resume downloads.  
Never mind,  I'll use gPodder instead.
gPodder doesn't seem to resume downloads either but they seem to be releasing new versions monthly so perhaps one day soon it will.  Fingers crossed.

---

### Post by steve101101 on 2008-06-11
worked great thanks

---

### Post by steve101101 on 2008-06-13
this is the second time i used bsmith1051 directions and they worked flawlessly again.

---

### Post by simonsonjh on 2008-06-19
Installation from subversion sources worked beautifully.  It's nice to have my Juice back.

---

### Post by regor210 on 2008-10-10
For an EZ install.
getdeb now has it.

[http://www.getdeb.net/release/3052](http://www.getdeb.net/release/3052)

---

### Post by Gyrotwister on 2009-03-12
gPodder 0.15.0 will now resume unfinished downloads.  

[http://www.gpodder.org/]("http://www.gpodder.org/")

Yippee!

---

### Post by irregardlessly on 2009-04-25
Just wanted to update, I upgraded from 8.04 to 8.10 today (my new rule is to always stay one release behind... Jaunty burned me on my ATI graphics card... hopefully that will get sorted out).  I did a format and reinstall and these directions worked perfectly.  Thanks!  Icepodder is a critical app for me.

---

### Post by bsmith1051 on 2009-05-08
FYI
I just upgrade from 8.10 to 9.04 and my existing copy of Icepodder stopped working.  I tried re-running the procedure I'd found but it didn't work.  

So now I've switched to using gPodder which is directly supported on Ubuntu.  The older version 0.14 is in the repositories, while a newer v0.15 can be downloaded directly from their web-site, [http://www.gpodder.org/](http://www.gpodder.org/)

---

