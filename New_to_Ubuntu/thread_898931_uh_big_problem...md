---
title: "uh big problem.."
date: 2008-08-23
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-23
i just restarted ubuntu and it still had graphics driver problems so i shutdown and restarted. i wanted to go to puppy linux but grub wouldnt let me. it would only load ubuntu. so i went to recovery mode. it loaded stuff and i went through it came up with my mouase beinge about 5 lines and split apart (very weird) and graphical problems. i went to last good boot, same problem. now no os but ubuntu will boot and ubuntu doesnt work. im on my laptop and how can i save my system.

---

### Post by kansasnoob on 2008-08-23
I don't understand. I have a Puppy USB drive that I can boot from, but you make it sound like you tried to plug in such a drive in the process of booting the hard drive.

Or do you have Puppy installed to your hard drive?

---

### Post by zamadatix on 2008-08-23
no i did a frugal install to the hdd for puppy(i od have it on usb but dont really use that). any other option on grub doesnt load. windows 64 bit puppy ubuntu kinda loads but it gives a messed up screen and doesnt really load then if i press the power button it turns off and if i try to turn on again bios doesnt load.... then i tried to boot form disc that worked. ubuntu recovery will load but i cant get it to check the filesystem it just reloads teh menu for recovery. also last good configuration wont load it also comes with a mesy screen

---

### Post by zamadatix on 2008-08-23
anyone? im kinda in a hurry and really would like my computer to boot properly. thanks

---

### Post by panhandle on 2008-08-23
Have you tried booting with Knoppix and examining your /var/log/messages?

---

### Post by zamadatix on 2008-08-23
no. i have only had linux for about a month. and the only live linux cd besides ubuntu is puppy. ill go into ubuntu and try what you said.

---

### Post by kansasnoob on 2008-08-23
Well, it kind of sounds like an xorg thing, but you're throwing me with the Ubuntu/Puppy thing!

If you can boot into Ubuntu recovery mode I'd do this in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by zamadatix on 2008-08-23
you can ignore puppy (it was an example of grub not working) im in the live cd does it matter if i do that here or should i do it off the hard drive?
ediy: i wnet ot the log folder and there are a bunch of files what am i suppose to do?

---

### Post by zamadatix on 2008-08-23
ive been having alot of problems latley. if i reinstall ubuntu grub will be reset wont it?

---

### Post by kansasnoob on 2008-08-23
> **zamadatix said:**
> ive been having alot of problems latley. if i reinstall ubuntu grub will be reset wont it?

Yes!

---

