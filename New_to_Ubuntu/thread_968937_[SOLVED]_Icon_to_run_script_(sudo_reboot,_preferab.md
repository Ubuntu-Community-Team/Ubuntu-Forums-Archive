---
title: "[SOLVED] Icon to run script (sudo reboot, preferably)"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-03
Hi, all

It's about four steps to head to my app launcher, find the restart icon, click it, and click the "Yes I'm freaking sure I want to reboot" button.  I have sent my restart button to the desktop as an icon, but clicking on it does nothing; it doesn't seem that it's retained its properties.  

How can I run a custom reboot script upon double-clicking a desktop icon?  That would be mighty handy (I'm envisioning other scripts I could run with other customized icons ;-)

I'd want to run a few common commands like:

sudo apt-get update
sudo apt-get upgrade
sudo updatedb
[close down applications azureus, kopete, amarok, kontact --cuz they're buggy on shutdown]
sudo reboot

---

### Post by ronocdh on 2008-11-03
Trying asking about this in the Desktop Environments forum. Personally what I'd recommend is installing something like Yakuake (I think in GNOME a comparable program is Tilde) and then typing a simple **sudo reboot**. GNOME-Do also supports commands like "lock" or "shutdown."

---

### Post by tarahmarie on 2008-11-03
I already use sudo reboot at the CL.  What I'd really like is to figure out how the icons work the way they do.  Why didn't sending my restart icon to the desktop work?

---

### Post by Paqman on 2008-11-03
You could write a little bash script. It's dead easy.

[Simple Bash scripts](http://floppix.ccai.com/scripts1.html)

Just make the script executable and sit it on your desktop. Pick a nice icon for it if you like.

---

### Post by FrostyFlames on 2008-11-03
He could also make a new shortcut that just runs "sudo shutdown -r now" (I like this better then "sudo reboot" just because I have more control and yes I know they do the same thing :) ).

---

### Post by tarahmarie on 2008-11-05
Thanks!  I've got the icon and script working now; all I need to know is how to change the icon for it.  What do I do?

---

### Post by tarahmarie on 2008-11-06
can I put an icon of my choosing on the desktop and attach it to my executable script?

---

### Post by tarahmarie on 2008-11-09
Does anyone know how to make an executable image?

---

