---
title: "Problem booting my desktop..."
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Serzedo on 2012-05-21
Hey guys!!

First of all, congrats, for having such a great community! I'm a fan of Lubuntu for some time.

I came here cause I'm having a problem...

As seen on this video:
[http://www.youtube.com/watch?v=rWYarWJFyDo](http://www.youtube.com/watch?v=rWYarWJFyDo)

This happens with all OS (from XP or others), currently I have Lubuntu. It works well for some time and then it stops loading the OS.

On this second video it loads... and sometimes it loads well, and runs flawlessly. By the way, when I pushed the Enter key, I found it was not related... or it wasn't a coincidence.
[http://www.youtube.com/watch?v=86_VFRUDvbY](http://www.youtube.com/watch?v=86_VFRUDvbY)

What could be wrong?

Thanks for all the help. ;)

---

### Post by wildmanne39 on 2012-05-22
Hi, if that was a message that said out of range please do:
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480

Then save and exit the document.


Then do:
```
sudo update-grub
```
Reboot
Thanks

---

### Post by Serzedo on 2012-05-24
SUPER!! It looks like it solved the problem. ;)

Many thanks dude!! :D

---

### Post by wildmanne39 on 2012-05-24
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by Serzedo on 2012-05-30
> **wildmanne39 said:**
> Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

Sorry. Noob thing. Done it. ;)

---

### Post by Serzedo on 2012-06-01
Were back again... it shows what is supposed to show, but most of the times the computer stalls on the "Lubuntu" loading screen. In order to work in the computer I must reboot it several times until it loads correctly.

The problem is back again... the same as the other OS's...:(

---

### Post by wildmanne39 on 2012-06-01
Hi, have a look at this link and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Please read it carefully, it has several options to try.
Thanks

---

### Post by inashdeen on 2012-06-01
Hi there, is this problem you are saying consistent with other OS? 
I suggest that it may be a hardware problem. not sure if it is identical, but once my lenovo had quite a similar problem. i cant boot to my os unless i do it several time. i went to the technician and they told my it is related to power source. he fix it and i dont have the problem no more

---

### Post by Serzedo on 2012-06-06
> **wildmanne39 said:**
> Hi, have a look at this link and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Please read it carefully, it has several options to try.
Thanks

I will read it. Thanks.

> **inashdeen said:**
> Hi there, is this problem you are saying consistent with other OS? 
I suggest that it may be a hardware problem. not sure if it is identical, but once my lenovo had quite a similar problem. i cant boot to my os unless i do it several time. i went to the technician and they told my it is related to power source. he fix it and i dont have the problem no more

Yes, it makes the same with any OS I use, sometimes it even stops on the motherboard splash screen. I thought it could be an hardware issue... but my thought went to the hard drive!

But that could be it!! Thanks. :)

---

### Post by Serzedo on 2012-06-21
OK. Now the PC doesn't do anything... I push the power on, he turns up, the lights os CPU and Power are on but it doesn't get out of it... I think this reveals that this is a hardware problem rather than software problem. ;)

"V"

---

