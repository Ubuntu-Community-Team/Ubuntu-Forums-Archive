---
title: "burning a bootable windows cd from ubuntu"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-11-16
Hey there. 
All my systems are Linux (Ubuntu 12.04) and I'd like to know how to burn a bootable windows cd from Linux. 
Would brasero work? or is there another specific program to burn an iso. Nero style?

Thank you!

K.m

---

### Post by sp-1070 on 2012-11-16
As far as i know itl work just fine with brasero

---

### Post by Kevin McCready on 2012-11-16
Is there a reason you don't use a USB stick?

I use
unetbootin

---

### Post by newb85 on 2012-11-16
> **Kevin McCready said:**
> Is there a reason you don't use a USB stick?

I use
unetbootin

That's backwards.  Unetbootin runs on Windows and creates USB for Linux.

---

### Post by kabukiM0n0 on 2012-11-16
> **Kevin McCready said:**
> Is there a reason you don't use a USB stick?

I use
unetbootin
Yup, because the system I was trying to install on doesn't run from USB. 

But it's okay - pretty straight forward - insert CD . right click .iso - write. :popcorn:

---

### Post by Kevin McCready on 2012-11-16
I have to correct you there. unetbootin runs fine with linux. 

I prefer to have an .iso on my system and just tell unetbootin to use that one in setting up the USB stick.

Whenever my wife has a problem on her microsoft machine I just boot a linux installation into RAM and fix it.

---

### Post by newb85 on 2012-11-17
[Pauses to remove foot from mouth]

---

### Post by squakie on 2012-11-17
> **Kevin McCready said:**
> I have to correct you there. unetbootin runs fine with linux. 

I prefer to have an .iso on my system and just tell unetbootin to use that one in setting up the USB stick.

Whenever my wife has a problem on her microsoft machine I just boot a linux installation into RAM and fix it.

So you're saying you can point unetbootin to a Windows install disk and it will burn it and it will be bootable, etc.?  I'm probably missing something, but I always thought unetbootin was for burning Linux disks.  The op wants to burn a Windows disk from ISO in Linux.

---

### Post by mlentink on 2012-11-17
> **squakie said:**
> I'm probably missing something, but I always thought unetbootin was for burning Linux disks.  The op wants to burn a Windows disk from ISO in Linux.

Which unetbootin will do. But Brasero will do it just as happily. 'Smatteroffact just right-click the iso in nautilus and than click on 'Burn to disk' will do fine.

---

### Post by squakie on 2012-11-18
I tried unetbootin to burn a Windows XP install disk ISO to usb.  Sure, unetbootin ran, but the boot was looking for linux boot files and didn't start any of the Windows XP things.

Also, when I right click the ISO in nautilus there is no "Burn to disk" option.

Perhaps the OP has run into some these also?

---

### Post by GreatDanton on 2012-11-18
You have to options:
1. Open up Brasero (or any other cd burner), select Burn Image, select the right iso and insert a cd/dvd.

2. Right click on the iso in nautilus, and select write to disc.

Regards.

---

### Post by monkeybrain2012 on 2012-11-18
??? Forgive my ignorance but Unetbootin only makes Linux bootable usbs and it does run in Linux, but the purpose is to create bootable usb for other Linux distros (which Ubuntu's live usb creator doesn't do). Moreover, Windows doesn't boot from Usb except for Windows8 (some people report they succeeded in making bootable windows 7 usb on the internet but doesn't just use unetbootin and friends who have tried said it doesn't work)  I haven't used Windows and Unetbootin for quite some times, is my info outdated?

---

### Post by mlentink on 2012-11-18
> **monkeybrain2012 said:**
> ??? Forgive my ignorance but Unetbootin only makes Linux bootable usbs and it does run in Linux, but the purpose is to create bootable usb for other Linux distros (which Ubuntu's live usb creator doesn't do). Moreover, Windows doesn't boot from Usb except for Windows8 (some people report they succeeded in making bootable windows 7 usb on the internet but doesn't just use unetbootin and friends who have tried said it doesn't work)  I haven't used Windows and Unetbootin for quite some times, is my info outdated?

Is that even the issue here? I thought OP wants to burn an iso to ***disk***. Which is easy to do by methods already described above.

---

