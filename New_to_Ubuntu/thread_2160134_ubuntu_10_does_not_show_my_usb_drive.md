---
title: "ubuntu 10 does not show my usb drive"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by cleancondenser on 2013-07-05
I have Ubuntu booted from the same USB drive
Ubuntu is working great,but 
I want to run Hiron's Boot CD ,
which is also located on the same USB Stick
I hit GO 
All that is visible is the Hard Drive ,the 
empty CD drive and a couple of empty
SD Card slots
I ALSO downloaded Hiron's Boot CD to
Ubuntu I selected save but can not find it 
after it downloads

---

### Post by newb85 on 2013-07-05
First, welcome to Ubuntu and the forums. 

Second, "Ubuntu 10" doesn't tell us what release you're using. It could be 10.04 our 10.10.

Third, neither one is supported anymore. Nothing older than 12.04 is. You're advised to stick with supported releases. 

With those out of the way, let's clarify your situation. Have you installed Ubuntu from the flash drive, or are you running it from the flash drive?

Also, what are the results when you run
```
 sudo lsusb 
```
in the terminal in Ubuntu?

---

### Post by fantab on 2013-07-06
Hiren's boot CD, is a bootable .iso, I believe. It should be burned to USB/CD/DVD and then booted.

---

### Post by CharlesA on 2013-07-06
If you are booting Ubuntu live off the USB stick, I don't think it will show up. If it does show up, it would show up like a hard drive.

---

### Post by dannyboy79 on 2013-07-06
what is your end goal with Hiron's Boot CD? because it appears to be a bootable cd with a ton of software in it, if you want to use those tools you'll need to boot your computer using that iso instead of ubuntu from the usb stick. you could use ubuntu to burn the iso onto a disk or create another bootable usb stick using Hiron's Boot CD (if that's even possible). you said you downloaded Hiron's Boot CD when you were booted within ubuntu, if it's firefox you were using the navigate to Hiron's Boot CD website and you choose to download it, did you check firefox's download folder?

---

### Post by newb85 on 2013-07-07
Hiren's is an independent system.  You can't run it at the same time as Ubuntu.

Also, you can't have two bootable .isos on the same USB, unless you manually configure the GRUB for the USB, which is a somewhat involved task.

---

