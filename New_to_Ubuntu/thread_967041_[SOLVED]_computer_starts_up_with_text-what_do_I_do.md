---
title: "[SOLVED] computer starts up with text-what do I do?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2008-11-01
Hi, I was trying to fix a lack of sound problem with the 21 kernel by pasting commands from another thread into the terminal and then rebooting. When it started again there was not the usual brown screen and then the log in name and password boxes, but a load of text. This finished with dell_desktop login: which I did and then added the password when prompted. Then I got some lines of information about Ubuntu and finally the opening line that appears when I open a terminal, waiting for a command.
What do I do now? What is the command to get into the computer like I used to? I assume I have enabled (or disenabled) something and once back into the computer I can reset it, If so, how do I do that?
BTW I have rebooted a few times to see if it would start properly with the older 19 kernel (generic and safe mode), but I seem to get the same text screen.
Simple, novice level explanations would be appreciated.

---

### Post by eolson on 2008-11-01
Just to make sure everything is working, try

start x

---

### Post by OutOfReach on 2008-11-01
Try:
```

sudo /etc/init.d/gdm start

```

---

### Post by teaker1s on 2008-11-01
if you have a link to the howto you were following it would greatly assist in resolving your issue.

 If your not sure or can't find the howto- most likely cause is that there is graphics driver configuration error

If you have seen writing on screen regarding xorg then try
```
sudo dpkg -phigh xserver-xorg
```

---

### Post by blackened on 2008-11-01
> **eolson said:**
> Just to make sure everything is working, try

start x

That should be ```
startx
```

I would first try what OutOfReach suggested.

---

### Post by Dermot Doyle on 2008-11-01
Hi, start x produced 'start:need to be root', OutOfReach's command produced 'command not found'.

---

### Post by eolson on 2008-11-01
try sudo startx or sudo the other command

---

### Post by teaker1s on 2008-11-01
```
sudo startx
```

---

### Post by Dermot Doyle on 2008-11-01
Wow, what a resource this forum is for a newbie like me. Right, OutOfReach's command didn't work, but startx (as opposed to start x) worked. Now I am in I have  an error panel thet says 'The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
It want to know if I want to delete the applet from my configuration.
Any ideas?

---

### Post by teaker1s on 2008-11-01
try
```
sudo /etc/init.d/gdm stop
```
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-desktop gdm
```
```
sudo /etc/init.d/gdm start
```

below the link discussing the error and various suggested fixes
[http://ubuntuforums.org/showthread.php?t=608767&page=6]("http://http://ubuntuforums.org/showthread.php?t=608767&page=6")

---

### Post by Megatog615 on 2008-11-01
Also note that it is a bad idea to use sudo for startx as it doesn't help to use root to run an X session. Root should only launch the login manager(gdm).

---

### Post by Dermot Doyle on 2008-11-01
Thanks a lot everyone. Seems to be working now. For the sake of understanding I think I found the problem, me. I was following the thread:

Comprehensive Sound Problem Solutions Guide v0.5e

I uninstalled and reinstalled the ASLA, but didn't notice that this would probably uninstall gdm and something else (I'm way past my understanding now). The thread gave a third command to reinstall these, but I didn't notice it and rebooted.
Oh well, my learning curve is looking suspiciously like a vertical line.
Cheers.

---

### Post by teaker1s on 2008-11-01
gdm is login manager, if you suffer any more issues with the error previously mentioned-thread I commented on will help:lolflag: Welcome

---

