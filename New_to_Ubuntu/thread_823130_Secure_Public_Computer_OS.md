---
title: "Secure Public Computer OS"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by malberga on 2008-06-08
I want to build a secure system that is used by the public. I want the user to be able to browse the Internet but have no access to any other part of the OS or any other software for that matter. 
The goal is to build a machine that will be in a coffee shop.
The other thing I would like to do is when the user does not move the mouse or enter anything on the keyboard for X minutes then a screen saver come on. Not just any screen saver, but an advertisment or several advertisments. 
I understand that these are two different requirments. But any help on either one would be great.
I am a Microsoft VB programmer that wants to "see the light of Linux" I would also like to have some input on what types of programming packages (Like Visual Studio) and what language I am assuming PHP which I have dabbled with. I appologise for being MS Brain dead. But I have been reborn :)
Thanks in advance for any help

---

### Post by PinkFloyd102489 on 2008-06-08
Ubuntu has kiosk programs, which may help you.

---

### Post by Paqman on 2008-06-08
I've heard of [Open Kiosk](http://openkiosk.sourceforge.net/), although i've never used it.

---

### Post by starcannon on 2008-06-08
Check this out:

[KDE Kiosk Mode]("http://developer.kde.org/documentation/tutorials/kiosk/index.html")

[KDE Kiosk Tutorial]("http://developer.kde.org/documentation/tutorials/kiosk/index.html")

Be sure to google around, you may find something for gnome as well, but it looks like KDE makes this pretty simple.

---

### Post by xravexheavenx on 2008-06-08
Try just booting off the LiveCD.  I have done it in a church youth center for their PCs and that way no system files or settings can be changed.  Also, an installation of Ubuntu would be fine because most system settings cannot be changed without root privileges. 

As far as setting the screensaver, you will have no problems with that.  It is easy to work with within the display settings.

Also, welcome to UbuntuForums!  :)

---

### Post by starcannon on 2008-06-08
downside with just running from livecd is your stuck at the speed of an optical drive :(

---

### Post by xravexheavenx on 2008-06-08
> **starcannon said:**
> downside with just running from livecd is your stuck at the speed of an optical drive :(
Very true.

Definitely try out kiosk mode or just do a clean install and let it ride.  Most of the users won't know how to navigate far from Firefox or OpenOffice because Microsoft had brainwashed them.

---

### Post by malberga on 2008-06-09
The CDRom is way to slow I agree, but also not secure. someone can take the CD. The system has to be bullet proof, since the machine will be unattended. I'll have to look into the Kiosk solution. The idea of a screen saver is not exactly a screen saver to say. I was invisioning a type of page that would run random videos, one might talk about how this machine is running on Linux Ubuntu a Microsoft Alternitive. While I am thinking about it, it would be cool to let anyone burn a LiveCD so they can take it home and experience the freedom.
looks like I need to start making an outline of the project.

User can Browse the Internet
User can Create Ubuntu LiveCD
User can download to USB
No booting from CD, USB or Floppy
Password protect Bios

---

### Post by starcannon on 2008-06-14
> User can Browse the Internet
User can Create Ubuntu LiveCD
User can download to USB
No booting from CD, USB or Floppy
Password protect Bios 

[B]User can Create Ubuntu LiveCD 
User can download to USB[/B]
Solution: System-->Administration-->Users and Groups--Create a limited user account, then add any groups that account needs.

[B]No booting from CD, USB or Floppy
Password protect Bios[/B]

Solution: Set up to only boot from HDD in bios, and set the Bios password in there while your at it.

Oh and while your at it, have the thing either email you are keep a log of root, and sudo attempts. maybe even have the machine go into a lockdown mode if one gets the sudo or root password wrong 3 times. Just some thoughts.

Sounds like a great project, and you've definitely chosen the right OS to handle this, Linux was built for security, you can custom lock it down to your finest details, you can even password protect file folders in a /home/user directory. Have fun, and if you know some high school kids that are willing to stress test it for you it wouldn't be a bad idea to let them have their way with it for a week and tell you what they broke, how they broke it, and then seal up those holes to :)

---

