---
title: "Installation Error"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by nick17 on 2012-08-21
I have tried to install the newest desktop Ubuntu on a disk and when I do, I get all the information in and when I hit continue on the window that wants your name and password, even if there is space on the download bar; the window goes away and then a window pops up and says that the installer incountered an unrecoverable error. Other times it will just shut down and try to reboot.

---

### Post by anewguy on 2012-08-21
I assume you mean installing to a hard disk on your PC.  I also have to assume you partitioned your disk allowing room for Ubuntu.  I don't know what the true minimum is, but I would recommend at least 10gb of disk space.

What are the specs of your PC?

---

### Post by nick17 on 2012-08-21
I have an 80gb hard drive, a 1.1 gigahertz cpu, an Anthlon XP 1800+ mother board and 2 gb ram.

---

### Post by ajgreeny on 2012-08-21
If you are using a live CD boot to the desktop using the "try without installing" option, then open a terminal with Ctrl+Alt+T and run the command ```
sudo apt-get remove ubiquity-slideshow-ubuntu
```Wait for that to finish then run the installation again.

It appears that there is a bug on some hardware that causes the slideshow to crash and take the installer with it, probably leaving you with a spinning cursor, but nothing happening.

I had the same thing in Ubuntu, Xubuntu and Lubuntu live CDs; removal of the slideshow in the live system did the trick.

---

### Post by nick1221 on 2012-08-21
It works my problem is solved! Thank you!

---

### Post by ajgreeny on 2012-08-21
Great!

Go to **thread tools** at the top and mark as solved please.

---

### Post by anewguy on 2012-08-22
> **ajgreeny said:**
> If you are using a live CD boot to the desktop using the "try without installing" option, then open a terminal with Ctrl+Alt+T and run the command ```
sudo apt-get remove ubiquity-slideshow-ubuntu
```Wait for that to finish then run the installation again.

It appears that there is a bug on some hardware that causes the slideshow to crash and take the installer with it, probably leaving you with a spinning cursor, but nothing happening.

I had the same thing in Ubuntu, Xubuntu and Lubuntu live CDs; removal of the slideshow in the live system did the trick.

This is great to know!  Thanks!

---

### Post by Wim Sturkenboom on 2012-08-22
> **ajgreeny said:**
> It appears that there is a bug on some hardware that causes the slideshow to crash and take the installer with it...
Any source for that?

---

### Post by ajgreeny on 2012-08-22
> **Wim Sturkenboom said:**
> Any source for that?
Here you go [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568) which also points to several duplicate bugs of the same thing.  Sorry, I meant to add that reference to my first post.

Perhaps related to AMD cpu or ATI video cards, both of which I have.

---

### Post by Wim Sturkenboom on 2012-08-22
Thanks for the link.

---

