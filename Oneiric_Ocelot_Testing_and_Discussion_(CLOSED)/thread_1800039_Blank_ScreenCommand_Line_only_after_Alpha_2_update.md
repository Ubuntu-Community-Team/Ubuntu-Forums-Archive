---
title: "Blank Screen/Command Line only after Alpha 2 update"
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Smithie on 2011-07-08
So here was my path to Alpha 2.  I used the update manager on Alpha 1 today, but things got screwy and I could not reopen update manager to check in ubuntu 3d or 2d if the full upgrade to Alpha 2 was now available to me.

Hoping to fix this, I opened the terminal and did a "sudo aptitude udpate", and then "sudo aptitude upgrade".  I was asked to select gdm or lightdm for graphics, I picked the Lightdm.  System asked for a restart, which I did, but now I only arrive at a blank/black screen after the constant "udev error".

Currently, I can only open a command line.... but have no idea what to do next.  Any help would be greatly appreciated, I am a noobie too, so please give me the details on instruction.  Thanks!!!

---

### Post by Smithie on 2011-07-08
Have tried unplugged the second monitor, and purging/re-installing nvidia-current.  Still stuck with blank/black screen and command line.

---

### Post by lucazade on 2011-07-08
Have you tried to simply restart lightdm?
sudo service lightdm restart (or stop and start if it complains)

if you don't see the commandline switch to another virtual terminal with ctrl+alt+F1 (or F2..), login and restart lightdm

---

### Post by Smithie on 2011-07-08
Restarting or Stop/Starting lightdm just closes the terminal and brings me back to a blank screen.

But....When I stopped lightdm, I was brought back to the load screen, which was frozen on "checking battery state" - although this is a PC Tower....but this glimmer of hope passed, and when I re-opened the terminal and started lightdm again, blank/black screen.

---

### Post by ScislaC on 2011-07-08
If it's actually a LightDM issue, which it appears it may be, you could always run "sudo dpkg-reconfigure gdm" and set gdm as the default for the time being.

---

### Post by jfernyhough on 2011-07-08
I have to occasionally reinstall the proprietary graphics drivers, e.g.

$ sudo aptitude reinstall fglrx
$ sudo service gdm restart

---

### Post by Smithie on 2011-07-08
ScislaC, Thanks!  I was wondering if switching back would help, but was unsure how to do it.  Things are at least functioning again in gdm, now I just need to figure out what this underlying graphics issue is which has been giving me pretty constant issues since Natty......

---

