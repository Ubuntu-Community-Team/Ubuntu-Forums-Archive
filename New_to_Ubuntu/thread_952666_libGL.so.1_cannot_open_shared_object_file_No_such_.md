---
title: "libGL.so.1: cannot open shared object file: No such file or directory"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by wowfunhappy on 2008-10-19
Hello. I recently have been having a problem with a few of my programs. Whenever I click on these select programs, nothing happens- that is, the program won't start. 

In an attempt to find the issue, I tried running these programs from the command line, and they all yield the same error message: 

```
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

Does anyone have any idea what the problem is, and/or how I can fix it?

I am running Xubuntu Hardy. My graphics card is an ATI Radeon 9500.

Thanks in advance!

---

### Post by cmnorton on 2008-10-19
I believe it means you've got to go find that library -- or something that sounds very much like it -- in your Synaptic manager, and download it.

---

### Post by wowfunhappy on 2008-10-19
I searched for "libGL.so.1" in synaptic before posting this thread. Doing so yields three packages- non of which can be installed without removing several other important looking packages, one of which being "xubuntu-desktop" which I definitely do not want to get rid of for obvious reasons.

The odd thing is that these programs USED to work fine- they just sort of stopped working a few days ago.

---

### Post by markbuntu on 2008-10-19
If you are trying to install a driver from ati on hardy amd64, you need to make a link to LibGL because it is not where the driver looks for it. These are some directions from the guide at cchtml

If that command fails to find libGL.so.1, check your /usr/lib directory for libGL.so with:

ls /usr/lib/libGL*

If you can see libGL.so in that list then:

sudo ln -s /usr/lib/libGL.so /usr/lib/libGL.so.1

The full guide is here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The new 8.10 driver is out now and installs with the automatic installer. Directions for that are also in the link above.

---

### Post by aboud on 2008-12-07
thank you for the useful information, 

in fact i have all the files: 
libGL.so
libGL.so.1 .. and so on  in /usr/lib/
but i still get the error in this post title. :confused:

---

### Post by jdthood on 2011-12-21
Tip:

/usr$ find lib32 -name libGL.so.1
lib32/mesa/libGL.so.1
/usr$ LD_LIBRARY_PATH=/usr/lib32/mesa google-earth

---

### Post by AmanoJack on 2012-05-19
**May 19, 2012**

My Ubuntu 12.4 installation is still pretty pristine on this drive,  so I would think that a lot of people will probably have this problem right out of the box. (Does this make it a  bug?). You can just follow the steps in bold if you don't want an explanation. The  problem is that Ubuntu can't find the file libGL.so because it either  hasn't been installed, or - more likely - its someplace unexpected. (In  my case, it turned up in the directory /usr/lib/fglrx/) If you can't get your desktop environment set up properly, or can't run a graphics  intensive program like World of Warcraft, this may be the problem.

**Step 1:**
Open a terminal (xterm) and type:
**ls /usr/lib/libGL***
This lists the files in the /usr/lib/ that begin with libGL.
("ls" means "list" and  "libGL*" means anything that begins with libGL)
If  you don't see a list of files, the file you need is either in another  directory or hasn't been installed. If you get a list of files, go to  Step 3.

**Step 2:**
Type this in your terminal window:[B]
ls /usr/lib/fglrx/libGL*[/B]
This lists the files in the /usr/lib/fglrx/ that begin with libGL.
If  you still don't get a list of files, you will either have to find the  file elsewhere, or install it. I can't actually remember how I found the  file, but perhaps someone else  can help with that. It was already installed on my system, so I can't  help with installation if that turns out to be the problem in your case.
 
**Step 3:**
Find the most recent version of the file. At this time  the newest version of the file is libGL.so.1.2, but this will change  over time. The current version will have the highest number at the end.

**Step 4:**
Type this in your terminal window:
**sudo ln -s /usr/lib/libGL.so /usr/lib/fglrx/libGL.so.1.2**

"sudo" runs the command as a superuser.
"ln -s /usr/lib/libGL.so" creates a file called libGL.so and makes it a link to the file your system needs.
The second part of the command tells your computer what the other file is.
If  your file is in another directory, or has a different version number,  substitute that here. For instance: "sudo ln -s /usr/lib/libGL.so  /usr/lib/directoryname/libGL.so.1.4"

This is just a slightly more detailed explanation based on previous posts, but I thought it might make it easier for the next person. Good luck!

---

### Post by nothingspecial on 2012-05-19
Thanks for the extra information.

This thread is very old however.....

---

