---
title: "[SOLVED] Just installed a program but can't find it!"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by naggis on 2008-06-03
I bet this is a very silly question but please bear with an ignorant newbie.
I have just installed a program - wakeonlan using Synaptic Manager which now confirms that it is installed. How do I run this program - its not showing in any of the Application folders. Do I have to run a terminal? If so what scrip do I type? Once I find the program presumably it will not be difficult to drag it to a desktop icon.
Sorry is this is all to simple - please put me out of my misery.
Thanks

---

### Post by spiderbatdad on 2008-06-03
try: ```
man wakeonlan
```for instructions.

```
sudo updatedb
locate wakeonlan
```to search, or

```
find wakeonlan
```a slower search.

Or the graphical search tool under the places menu...set file system for search path.

---

### Post by ibuclaw on 2008-06-03
Sure, and you don't ever need to excuse yourself in anything in the forums.
We are all here to learn off each other.

WakeOnLAN is a terminal based application. But you can easily create a launcher on your desktop to carry out a specific task.



To find out about how to use the application, open up a terminal and type in:
```
wakeonlan
```
And some basic help info will be printed.

Or, for a more indepth overview of how to use the software, read the manual.
```
man wakeonlan
```

Regards
Iain

---

### Post by hyper_ch on 2008-06-03
as it is a cli command/program there will not be any menu entry.

---

### Post by naggis on 2008-06-03
Thanks guys. I have been able to find the manual and readme files which do make some sense. But as a lifelong Windows user it does take a bit of sorting to use a terminal - ie finding all the relevant information and getting it written correctly. Still here we go.
Maybe there is a better way to wake a Windows pc/server. Perhaps a further post on that subject may be more enlightening to me

---

### Post by naggis on 2008-06-03
To tidy up this thread. 
Having read the manual, I managed to get the program to work - ie it took my desktop out of its sleep mode.
But then, with some help from another thread, I made an icon for the desktop which will obviate the need to type in a long MAC address. 
It is true, you do learn something every day.
The best bit about using Ubuntu is that there are so many of you folks out there who are more than willing to help - at the drop of a hat. It certainly makes me feel part of a community.
Thanks again

---

