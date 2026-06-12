---
title: "New to ubuntu and programming"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by olivier8 on 2014-08-14
What are the steps to installing a progamming language?  For example, the python programming language?  I went to the python website [https://www.python.org/downloads/release/python-341/](https://www.python.org/downloads/release/python-341/)  I do not see a download link for the operating system I want, which is ubuntu linux.  Do I choose the source release version?

---

### Post by olivier8 on 2014-08-14
Also, is there a more beginner oriented place to post such questions?  Not sure if I should have posted here.

---

### Post by mörgæs on 2014-08-14
Hi, welcome to the fora.

Your thread has been moved. Feel free to use the report button next time, also if it concerns your own thread.

---

### Post by sotiris2 on 2014-08-14
Try ```
sudo apt-get install python
``` in a terminal window. It will ask for your password, type it in and press enter, it won't show any feedback such as *** as you type but its ok. 
For python check out:
[http://www.learnpython.org](http://www.learnpython.org)
[http://en.wikibooks.org/wiki/A_Beginner's_Python_Tutorial](http://en.wikibooks.org/wiki/A_Beginner's_Python_Tutorial)
or if you have a book yourself.

---

### Post by Impavidus on 2014-08-14
Isn't python installed by default? Lost of parts of Ubuntu depending on it. Update-manager for example.

Anyway, downloading software from websites is not the preferred way of installing stuff on Ubuntu. There is the software centre (good for beginners), synaptic or the command line (as indicated by sotiris2). They all offer the same software from the Ubuntu repositories, just different interfaces. If you install software using any of these, you have the easiest way of installing, know the software will work (most of the time), know that you won't get malware and you'll get automatic updates.

Edit: And it will handle dependencies automatically.

---

### Post by Jonathan Precise on 2014-08-14
Python should be installed by default in ubuntu.

Python3 should also be installed in ubuntu.

The link you gave is python3, not python. The difference is that python is version 2.7 and python3 is version 3.3 or 3.4.

---

### Post by Paulgirardin on 2014-08-14
There is a series of Python tutorials here: [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by grahammechanical on 2014-08-14
If you are using Ubuntu 14.04 you will find python 2.7 installed by default. I have it on my system. Search for it in the software centre. Also in the software centre but not installed by default is IDLE - Integrated Development Environment for Python (using Python- 2.7)

Regards.

---

### Post by olivier8 on 2014-08-14
I was hoping to upgrade my ubuntu to version 14.04 from 13.04 using the software updater.  Some updates for some of the applications are present, but the update to 14.04 is not present.  Is there a different way to update to 14.04?

---

### Post by ian-weisser on 2014-08-14
There used to be, but you missed it.
When a version reaches End Of Life, the repositories are withdrawn.
13.10 was withdrawn on July 17, 2014. You can no longer upgrade to it.

Upgrades can only run version-to-next-version: 13.04 to 13.10 to 14.04.
You cannot skip versions.
The sole exception is that you can upgrade from LTS to LTS: 12.04 to 14.04.
But 13.04 was not an LTS.

You cannot use Software Updater or Update Manager (or Synaptic or apt-get or any other method) to upgrade from 13.04 to 14.04.
If you want 14.04, the only supported method is reinstalling from a fresh 14.04 install media.

---

### Post by olivier8 on 2014-08-15
Thank you Ian.  That really clears up some frustrations I was having.

---

### Post by Rob Sayer on 2014-08-16
After a spell of DE and distro hopping on my netbook prior to xubuntu 14.04 being released (some hardware issues that are fixed in the newer kernels), I've found I prefer to reinstall linux rather than update.  It's more reliable.

I highly recommend installing with a separate /home partition.  You can then reinstall/update releases while keeping your data and user settings.  I find the performance is better too.  Just don't reformat /home when reinstalling and back up your data anyway.

---

