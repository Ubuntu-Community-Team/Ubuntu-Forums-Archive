---
title: "Got 8.04 but cant get into LiveCD to reinstall"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Dj Dutchman on 2008-05-03
Hi, i recently installed 8.04 and in my attempt to setup a home server I must have made some mistakes along the way & now I would like to reinstall Xubuntu but when I put the LiveCD in it still boots into my installed Xubuntu (on the HDD), even though my CD drive is higher than my HDD in boot priority. Even if I completely remove HDD from the boot list it still boots from the HDD...

Help...

---

### Post by suprfish on 2008-05-03
Does it at least attempt to boot from CD? (do you hear the drive whirring while booting)? Did you write the CD yourself?

---

### Post by Monicker on 2008-05-03
Sounds like an issue with your BIOS, or the CD drive itself.  Can you read a CD which is in the drive while you are in Ubuntu?

---

### Post by Dj Dutchman on 2008-05-03
It does 'whir'. I did write the disk my self but it installed fine & I checked the disk (from the LiveCD menu) & I just booted to liveCD on 1 of my other PC's. I'm gonna sound like a complete noob but how do I check the disk from Xubuntu side???

---

### Post by st33med on 2008-05-03
Hello DJ. When you say you cannot boot from the CD, did you set your BIOS to start from the CD? Was your hard-drive 'blank' when you installed Xubuntu? What did you do to screw up your Xubuntu install?

---

### Post by suprfish on 2008-05-03
> **Dj Dutchman said:**
> It does 'whir'. I did write the disk my self but it installed fine & I checked the disk (from the LiveCD menu) & I just booted to liveCD on 1 of my other PC's. I'm gonna sound like a complete noob but how do I check the disk from Xubuntu side???

Stick the disk in the drive and see if you can mount and explore it, there may have been corruption when your first wrote it or ...

---

### Post by Dj Dutchman on 2008-05-03
The 1st time I set it to start from CD, the 2nd time I removed all references of the hard drives (i forgot to mention, I have 2 - one with xubuntu & the other is blank). No, the HHD wasn't blank when I installed, t had an xubuntu 7.10 install which I wrote over...

---

### Post by st33med on 2008-05-03
Hrm. Yeah, you might want to reburn OR try to manually tell the BIOS to boot from the CD by first looking at the buttons you can press, then reboot and press the button that says something about boot (Ex: 'F12 = Boot Menu') *rapidly*. Then, tell it to boot off the CD.

---

### Post by Dj Dutchman on 2008-05-03
before i try that, I just tried to mount the drive with

```
mount /dev/cdrom
```

I have NO idea if this is the right command but I get a 'No medium found' error message...

---

