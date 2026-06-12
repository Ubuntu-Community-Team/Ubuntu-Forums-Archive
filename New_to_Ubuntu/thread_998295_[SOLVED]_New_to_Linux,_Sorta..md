---
title: "[SOLVED] New to Linux, Sorta."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by robm06 on 2008-11-30
Hey everyone!

This is my first post on Ubuntu Forums and while it's not my first time playing with Linux, it is with this computer. So I've been researching my computer the HP tx2525nr, part of the HP tx2000 series.

I'm hoping to be able to get it all working, but some of the posts were a little vague. Does the Wacom USB Driver set work or not? I saw search results that produced both answers. 

Anyways, while this isn't my first adventure into the world of Linux, I'm hoping it will stick this time. I'm very unsatisfied with Windows Vista Ultimate 64-bit and I've had decent luck with Ubuntu in the past but I've always left because of various programs that I was missing. Mostly I was finding it unable to work without iTunes and Microsoft Office, but I believe I can VM windows in Ubuntu and get iTunes working and there are great alternatives to Office that I'm getting better at. 

So does anyone have any real advice for me during this switch? Anyone know if this laptop will easily handle it better than Vista?

Thanks
RobM06

---

### Post by madsc89 on 2008-11-30
Welcome back to Ubuntu.

I haven't got any knowledge concerning your questions, but you should edit the thread title to explain what you want help with.

---

### Post by madsc89 on 2008-11-30
However, Ubuntu requires far from as much resources as Vista.
On the other side, support for newer laptops can be somewhat undeveloped. That is, it takes some time for drivers etc. to be written. How old is the computer and the USB device?

Also Wine could help you with some of your Windows applications. Popular programs like iTunes is bound to be working thorugh Wine, or there is an alternative...

---

### Post by Sealbhach on 2008-11-30
Is it the Wacom USB tablet? Looking at this link, that does work if you make some changes to the xorg.conf file.

[http://www.hightechsister.com/25/ubuntu-hardy-804-gimp-wacom-success/](http://www.hightechsister.com/25/ubuntu-hardy-804-gimp-wacom-success/)

I would suggest to try Ubuntu using the Wubi installer, for starters.

[http://wubi-installer.org/](http://wubi-installer.org/)

See what works and what doesn't.


.

---

### Post by robm06 on 2008-11-30
> **Sealbhach said:**
> Is it the Wacom USB tablet? Looking at this link, that does work if you make some changes to the xorg.conf file.

[http://www.hightechsister.com/25/ubuntu-hardy-804-gimp-wacom-success/](http://www.hightechsister.com/25/ubuntu-hardy-804-gimp-wacom-success/)

I would suggest to try Ubuntu using the Wubi installer, for starters.

[http://wubi-installer.org/](http://wubi-installer.org/)

See what works and what doesn't.


.

I believe the Wacom USB Tablet is what is used in this laptop. It's actually a tablet laptop that uses the Wacom hard-ware and after that right now I'm fairly lost. Wubi came around after I left Ubuntu awhile back, I'll need to try that out, sounds like a good way to get started, thanks!

This is the laptop, best buy link. [http://tinyurl.com/67lumh](http://tinyurl.com/67lumh)
It's not a brand new laptop, but not an older one either, I've had it since July myself but I believe it had been out awhile before that.

I had actually considered switching to an Apple Laptop instead of this laptop, but when I made my decision I thought I would eventually turn this into a Linux machine.

I'm hoping to drop Windows completely, especially before Windows 7 comes about.

Also I apologize that the topic name does not show that I have a question, I guess I should have thought of that beforehand.

---

### Post by NewJack on 2008-11-30
You may want to check out this thread (Sorry, I didn't have time to check all 11 pages):

[http://ubuntuforums.org/showthread.php?t=845911&highlight=wacom](http://ubuntuforums.org/showthread.php?t=845911&highlight=wacom)

Here is a HowTo to install Hardy on a TX2500 series Laptop

[http://ubuntuforums.org/showthread.php?t=873188&highlight=wacom](http://ubuntuforums.org/showthread.php?t=873188&highlight=wacom)

Here is also a HowTo link for Wacom Tablets:

[http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom](http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom)

Good Luck!

---

### Post by robm06 on 2008-12-01
> **NewJack said:**
> You may want to check out this thread (Sorry, I didn't have time to check all 11 pages):

[http://ubuntuforums.org/showthread.php?t=845911&highlight=wacom](http://ubuntuforums.org/showthread.php?t=845911&highlight=wacom)

Here is a HowTo to install Hardy on a TX2500 series Laptop

[http://ubuntuforums.org/showthread.php?t=873188&highlight=wacom](http://ubuntuforums.org/showthread.php?t=873188&highlight=wacom)

Here is also a HowTo link for Wacom Tablets:

[http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom](http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom)

Good Luck!

Thanks! I installed Ubuntu through Wubi a few minutes ago and while I havn't tried to set up the tablet portion of my laptop yet, it is already working very well on 8.10. Thanks for all the links, you've been a big help!

---

### Post by SunnyRabbiera on 2008-12-01
well what is so great about itunes that a linux alternative cant offer?
if its buying tunes then I say screw it, all itunes odes is give you DRM ridden files that if you transfer them to an ipod then technically you are breaking the law under the DMCA.
These days I can care less about "legal"

If its ipod support, well there are many tools for that und4er linux, but the thing is you should not be running a ipod in the first place.
For one apple gives us grief, two they dont even want linux users using ipods.
I say sell your ipod and get something more linux friendly, a sansa clip is almost as good as a ipod in my opinion at least when it comes to MP3 players.

---

### Post by NewJack on 2008-12-01
Glad to hear it.  

If you don't mind, just post what helped you get things up and running.  I am sure someone else may come across the same issue as you and may need a nudge in the right direction.  Especially the tablet portion.

Also if it has been (or once it is 100%), make sure you mark the thread as SOLVED.  That helps others know there was some success too.

Thanks!!!

---

### Post by robm06 on 2008-12-01
> **SunnyRabbiera said:**
> well what is so great about itunes that a linux alternative cant offer?
if its buying tunes then I say screw it, all itunes odes is give you DRM ridden files that if you transfer them to an ipod then technically you are breaking the law under the DMCA.
These days I can care less about "legal"

If its ipod support, well there are many tools for that und4er linux, but the thing is you should not be running a ipod in the first place.
For one apple gives us grief, two they dont even want linux users using ipods.
I say sell your ipod and get something more linux friendly, a sansa clip is almost as good as a ipod in my opinion at least when it comes to MP3 players.

I'm a big fan of the iPhone myself, that's the only reason I really want any iTunes support at all. I have a jailbroken device that I enjoy playing with. I could care less about buying music from them anymore.

> **NewJack said:**
> Glad to hear it.  

If you don't mind, just post what helped you get things up and running.  I am sure someone else may come across the same issue as you and may need a nudge in the right direction.  Especially the tablet portion.

Also if it has been (or once it is 100%), make sure you mark the thread as SOLVED.  That helps others know there was some success too.

Thanks!!!

I guess I can mark THIS thread as solved now, because I do have Ubuntu working. The Tablet portion of my laptop isn't up and running yet but from the look of the posts in this thread it will just be a matter of me sitting down and installing some files and editing a file or two. 

As far as what I've done so far? I just downloaded the 64-bit 8.10 ISO, burned it to the CD, installed it with Wubi. During the last stages I had a short kernal panic that restarted the system that freaked me out and my system rebooted itself, and I've not had that happen again.

I have an HP Pavilion tx2525nr and this has been the easiest install I've ever had with Ubuntu. While I do not have the tablet portion up and running, it is usable as a laptop and it's running great with the 64-bit version. I'm extremely happy with it and I can see moving to this soon in my future :)

I thank you all for helping me and I hope that I can one day become useful to this community because I plan to stick around and try to help where I can, after I learn it myself that is! :lolflag:

---

### Post by NewJack on 2008-12-01
> **robm06 said:**
> I thank you all for helping me and I hope that I can one day become useful to this community because I plan to stick around and try to help where I can, after I learn it myself that is! :lolflag:

Welcome to the Community!

---

