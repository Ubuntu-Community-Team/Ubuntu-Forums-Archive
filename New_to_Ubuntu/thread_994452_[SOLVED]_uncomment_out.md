---
title: "[SOLVED] uncomment out"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by scorey1609 on 2008-11-26
Hi,

I'm not exactly new to Ubuntu, but I ran into a usb issue while running VirtualBox and the solutions to it talk about having to "uncomment out" something in this file /etc/init.d/mountdevsubfs.sh.

My question:  What does "uncomment out" mean?

Thanks!

----Edit-----

For reference, the form I'm using is here:  [http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/](http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/)

---

### Post by halitech on 2008-11-26
in most files, if you put a # in front of a line that is commenting it out

---

### Post by aeiah on 2008-11-26
yea, scripts are made up of a series of commands and instructions. any line that starts with a # is ignored by the interpretor / operating system. if you uncomment a line, it means you remove the # so as it becomes readable to whatever is executing the script (virtualbox, in this case i presume).

---

### Post by jemate18 on 2008-11-26
> **scorey1609 said:**
> Hi,

I'm not exactly new to Ubuntu, but I ran into a usb issue while running VirtualBox and the solutions to it talk about having to "uncomment out" something in this file /etc/init.d/mountdevsubfs.sh.

My question:  What does "uncomment out" mean?

Thanks!

----Edit-----

For reference, the form I'm using is here:  [http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/](http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/)


#this line is a comment
this line is not a comment

Just remove the '#' to uncomment the line

---

### Post by scorey1609 on 2008-11-26
all right, thanks y'all...  It didn't work for for making the VirtualBox error go away, but I learned something!

---

### Post by jemate18 on 2008-11-26
at least it solved the UNCOMMENT Thin.. please mark this thread as SOLVED..

Maybe you could try this VBOX tutorial
> [https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

---

