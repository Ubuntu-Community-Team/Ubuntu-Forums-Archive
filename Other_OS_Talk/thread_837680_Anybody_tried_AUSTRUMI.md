---
title: "Anybody tried AUSTRUMI?"
date: 2008-06-22
forum: Other OS Talk
---

### Post by cardinals_fan on 2008-06-22
Look at this: [http://cyti.latgola.lv/ruuni/](http://cyti.latgola.lv/ruuni/)

This looks like a really interesting distro.  Has anybody tried it?

---

### Post by kk0sse54 on 2008-06-22
Sorry mate but I can't exactly read the link

---

### Post by cardinals_fan on 2008-06-22
> **C!oud said:**
> Sorry mate but I can't exactly read the link
Don't speak Latvian? :)

No problem, just click the "EN".  See my pic:

[[img]http://xs228.xs.to/xs228/08250/7792.gif.xs.jpg[/img]](http://xs.to/xs.php?h=xs228&d=08250&f=7792.gif)

---

### Post by kk0sse54 on 2008-06-22
](*,) i see it now...:lolflag:
from what I read it sounds really cool. I'll have to try it on my old dell when I get the chance.

---

### Post by init1 on 2008-06-22
I tried it. It's ok. I could never get it installed to my pen drive though.

---

### Post by cardinals_fan on 2008-06-22
> **init1 said:**
> I tried it. It's ok. I could never get it installed to my pen drive though.
Doesn't matter to me, as I've yet to see a machine that boots from a pen drive.

---

### Post by kk0sse54 on 2008-06-23
I have DSL installed on my pen drive which I take with me everywhere. Has booted fine on every computer I have ever tried it on except for my laptop.

---

### Post by zmjjmz on 2008-06-23
PUD looks like a good pendrive distro.
Anything that boots to RAM really, so Slitaz Austrumi DSL and Puppy are all contenders too.

---

### Post by ugm6hr on 2008-12-03
> **init1 said:**
> I tried it. It's ok. I could never get it installed to my pen drive though.

I've just given v1.8.0 a whirl.  I think it's great.

In fact, I never burnt a CD, just used unetbootin to write the .iso to a 128MB FAT32 USB stick.  Reboot and select "al" to boot.

Just took a minute to find out how to restart X in English (default Latvian): Left-click desktop: Istatlejumi -> Valodas.
 
Very fast when loaded to RAM, and looks great. Only have DSL 4.0, Slitaz 1.0 & Puppy 2.14 to compare, but I think it is slicker than any of them.

Only problem is network setup: wired is OK; only wifi driver is Intel kernal driver - no good on my laptop.

[IMG]http://cyti.latgola.lv/ruuni/screenshoots/small/a-180.jpg[/IMG]

---

### Post by Sorivenul on 2008-12-03
How did I miss this thread for so long?  
I've tried it, and find it a solid little system.  I've never been a fan of DSL or Puppy really, and this fits my light needs perfectly.  The default Latvian keeps me from suggesting it for lower-end systems, though.

---

### Post by ugm6hr on 2008-12-04
> **Sorivenul said:**
> The default Latvian keeps me from suggesting it for lower-end systems, though.

Have you done a HD install, or run from LiveCD/USB?  Presumably a HD install can be customised with English as default.

There is also a built-in "Customise ISO" application; haven't tried it yet, but it seems straightforward to create an English iso.

---

### Post by Sorivenul on 2008-12-04
> **ugm6hr said:**
> Have you done a HD install, or run from LiveCD/USB?  Presumably a HD install can be customised with English as default.

There is also a built-in "Customise ISO" application; haven't tried it yet, but it seems straightforward to create an English iso.

I have, and a custom ISO isn't an issue either.  Changing the language isn't a challenge for me, it's more a showstopper when it comes to me suggesting it to other users with lower-end systems.

---

### Post by christopher1 on 2008-12-04
No dude i have not tried but i hope i ll check with it now...

---

### Post by Davidpeter on 2008-12-04
Yes i tried it.... its really very interesting...

---

### Post by zmjjmz on 2008-12-04
> **Sorivenul said:**
> I have, and a custom ISO isn't an issue either.  Changing the language isn't a challenge for me, it's more a showstopper when it comes to me suggesting it to other users with lower-end systems.

Well you could create a custom English ISO and then host it and point towards that package when someone asks for a suggestion.

I'm going to try this out over the weekend.

---

### Post by ugm6hr on 2008-12-04
> **zmjjmz said:**
> Well you could create a custom English ISO and then host it and point towards that package when someone asks for a suggestion.

I'm going to try this out over the weekend.

Only issue I can find is the lack of support documentation for it.

Additionally, registering for their forum takes a little ingenuity, since all the details are labeled in Latvian.

EDIT: I found this, which appears to be supported by 1 person: [http://austrumi.mypunbb.com](http://austrumi.mypunbb.com)

EDIT2:
> **zmjjmz said:**
> Well you could create a custom English ISO
I managed to edit my unetbootin created LiveUSB very easily to default to English by making changes to the Unetbootin syslinux.cfg:
```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 5

label ubnentry1
menu label Austrumi-English
kernel /isolinux/bzImage
append initrd=/isolinux/initrd.gz dousb lang_en

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit dousb

label ubnentry0
menu label al
kernel /isolinux/bzImage
append initrd=/isolinux/initrd.gz dousb
```

I think that the same should be possible for the LiveCD iso isolinux / syslinux files (just add *lang_en* to the end of the append line):
Ref: [http://austrumi.mypunbb.com/viewtopic.php?id=356770](http://austrumi.mypunbb.com/viewtopic.php?id=356770)

I also managed to customise the Firefox startup preferences on the USB (to be preset for a proxy) by setting them in the LiveUSB, then copying the newly created /root/.mozilla folder to the compressed austrumi.tzg with File-Roller on the USB.

Discovered that the keyboard was set as Latvian... Alt+Shift switches to a US keyboard after booting.  Need to edit /etc/X11/xorg.conf to change that too. Unfortunately, just adding and xorg.conf file with "gb" as keyboard doesnt work.  Going to have to try this: [http://austrumi.mypunbb.com/viewtopic.php?id=353850](http://austrumi.mypunbb.com/viewtopic.php?id=353850)

---

### Post by ugm6hr on 2008-12-06
> **ugm6hr said:**
> Discovered that the keyboard was set as Latvian... Alt+Shift switches to a US keyboard after booting.  Need to edit /etc/X11/xorg.conf to change that too. Unfortunately, just adding and xorg.conf file with "gb" as keyboard doesnt work.  Going to have to try this: [http://austrumi.mypunbb.com/viewtopic.php?id=353850](http://austrumi.mypunbb.com/viewtopic.php?id=353850)

Trying to get the "gb" (UK) keyboard is proving a little difficult.

[http://austrumi.mypunbb.com/viewtopic.php?id=353850](http://austrumi.mypunbb.com/viewtopic.php?id=353850)

I tried using Ubuntu's xmodmap file (usr/bin/xmodmap) and copied it to /usr/bin/xmodmap in the austrumi.tgz archive.

I also used *xmodmap -pke > .Xmodmap* and copied that file to etc/X11/xinit/.Xmodmap in the same archive.

I have checked the contents of etc/X11/xinit/xinitrc.fvwm, which looks for .Xodmap in that location.

Unfortunately, the xmodmap command doesn't work (from Terminal either) in Austrumi, which is perhaps the problem.  Do I have to get a Slackware copy of the xmodmap executable file?

---

