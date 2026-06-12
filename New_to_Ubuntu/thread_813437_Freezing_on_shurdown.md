---
title: "Freezing on shurdown"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by jfh on 2008-05-30
Some time ago, I posted this thead re a problem I was having with Ubuntu 8.04:

Problem with Ubuntu 8.04 
I am using XP Serv. Pack 2, 3.40Ghz Intel Pentium4, 197 G free HD space, 2GB memory. I have installed previous versions of Ubuntu in VM and Virtual Box, but had uinstalled all of them before installing Ubuntu 8.04. At one point during the long installation (as a Windows program) a small blue box appeared with the legend: "Out of Range 46.4kHz/87 Hz". The box went away and the installation seemed to be completed sucessfully. However, when I tried to shut down Ubuntu, the blue box appeared again withe the same message. This time, my computer froze, and I had to unplug it in order to free it up and reboot it in Windows. Can anyone tell me the meaning and importance of the messge in the blue box and what, if anything, I can do to avoid a repeat of this problem. I enjoy using Ubuntu, but certainly don't want to have my computer freeze up each time I try to exit it.

With considerable help, I finally found out that it was a display problem, but never could determine exactly what what was causing the "overload".  However, in my looking, I found this Microsoft help site:
[http://support.microsoft.com/kb/315614](http://support.microsoft.com/kb/315614)
and I wondered if it is just possible that Windows is recognizing my Ubuntu installation as a large "game", thus causing the reaction described in the Microsoft site - since I opted to use the "installer" on the Ubuntu CD and install it as a Windows program

---

### Post by ajmorris on 2008-05-31
hi there, what did you use to configure your xorg.conf? Could you please post the contents of it, this error could be because your horizontal sync or vertical refresh rates are incorrect.

AJ

---

### Post by jfh on 2008-05-31
xorg.conf - ??  Sorry, I don't know what that means,  I set my display settings by going to Preferences (I think it was) in Ubuntu and by going to Display in the Control Panel in Windows.  I used the same settings in both.

---

### Post by ajmorris on 2008-05-31
hi, sorry, should have been clearer,
can you please open your /etc/X11/xorg.conf file, and post the contents here.

---

