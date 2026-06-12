---
title: "[SOLVED] how do I use the archive manager?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-06
i downloaded ndiswrapper but how does the extract work.  now I have a box and a folder on my desktop.  I don't like things on my desktop, so where should I put it?  when I open the folder it's just a bunch of files.  isn't this supposed to run?  It's an application right?  so why doesn't it apply?

---

### Post by LinuxFox on 2008-07-06
If you mean the default archive manager, you can use the Extract button on the toolbar to browse to where you want to save it.  You can even create a folder to put it in.  That's how I tried it and what I know.  I hope this helps.

---

### Post by adamogardner on 2008-07-06
how do I run it is wwhat I want to know most of all?

---

### Post by Tomatz on 2008-07-06
Where did you download ndiswrapper from?

You dont need to compile it, its in the repos (synaptic). If you cant get on the net, just download the two packages (below) and double click on them.


[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)

;)

---

### Post by adamogardner on 2008-07-06
i was instructed to download the more up to date version from sourceforge.  besides this is basic skills isn't it?  I ought to know how to download anyway.  It's just strange   so I tried this:

adamogardner@CRONUS:~$ tar zxvf ndiswrapper-verion.tar.gz
tar: ndiswrapper-verion.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
adamogardner@CRONUS:~$ 


there were some instructions in the folder   this was the first thing to do and once again nothingn is straight forward. here's the instruction:

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

---

### Post by Tomatz on 2008-07-06
> **adamogardner said:**
> i was instructed to download the more up to date version from sourceforge.  besides this is basic skills isn't it?  I ought to know how to download anyway.  It's just strange   so I tried this:

adamogardner@CRONUS:~$ tar zxvf ndiswrapper-verion.tar.gz
tar: ndiswrapper-verion.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
adamogardner@CRONUS:~$ 


there were some instructions in the folder   this was the first thing to do and once again nothingn is straight forward. here's the instruction:

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

You need to be in the same directory as the archive. If the archive is on the desktop change directory like this:

```
cd ~/Desktop
```

*That is case sensitive^ **(capital D)***

**Then**

```
tar zxvf ndiswrapper-version.tar.gz
```

;)

---

### Post by adamogardner on 2008-07-06
thankyou.  this is BS though.  Nothing should be so difficult.  Your first suggestion is the one I'm going with since it's the only one that wants to work.  maybe they'll update it for me.

---

### Post by Tomatz on 2008-07-06
> **adamogardner said:**
> thankyou.  this is BS though.  Nothing should be so difficult.  Your first suggestion is the one I'm going with since it's the only one that wants to work.  maybe they'll update it for me.

Because there are so many different Linux kernels when software is developed it is released as source so the user can compile it to fit his/her system. A package (.deb) is precompiled and packaged for your system so it can be easily installed much like a windows installer.

Even windows software needs to be compiled before it can be ran but because there is only one (or only a few) kernel/OS it needs to be compiled for, you never have to do this yourself.

Compiling is easy once you get the hang of it.

Usually compiling consists of (in order):

**cd /to/the/app/directory**

**./configure** (Will output any dependancys you may need to compile. Install them via synaptic)

**make** (compiles)
[B]
sudo make install[/B] (installs the compiled app)

Done ;)

---

### Post by adamogardner on 2008-07-06
thanks for the tip.  I AM getting the hang of this.  I'd rather compile than not compile any day of the week.  Cute baby btw.

---

### Post by Tomatz on 2008-07-06
> **adamogardner said:**
> thanks for the tip.  I AM getting the hang of this.  I'd rather compile than not compile any day of the week.  Cute baby btw.

Thanks :)

Once you get the hang of compiling once, you'll be able to do it a thousand times.

---

