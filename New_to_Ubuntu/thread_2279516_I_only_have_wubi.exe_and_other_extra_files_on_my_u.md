---
title: "I only have wubi.exe and other extra files on my ubuntu folder?"
date: 2015-05-23
forum: New to Ubuntu
---

### Post by rendell on 2015-05-23
I am trying to burn the ubuntu iso file to an sd card but I can't seem to find the iso file. The zip file has a .iso extension but I only see the wubi.exe which is about 1gb. I tried to install ubuntu with wubi but it gave me an error which says cannot download iso. :(

---

### Post by Vladlenin5000 on 2015-05-23
Hi and welcome.

Don't use WUBI. This tool was designed for the purpose of testing Ubuntu, not as a permanent installation. No longer developed and doesn't work in Windows 8.x.
Tells us about your specs instead so we can suggest the best course of action and eventually the Ubuntu flavor better suited for your hardware.

---

### Post by Bucky Ball on 2015-05-23
Welcome. There should be no zip file. Where are you downloading it from? Try [here]("http://www.ubuntu.com/download/desktop"). The download should consist of one .iso. That is it. No zip file. Now you create a disk image from that file on the SD. 

How are you attempting to burn the SD? What software are you using?

PS: Don't bother attempting to install Wubi. Although still available on the install disk, it is no longer supported by Canonical so avoid.

---

### Post by cariboo on 2015-05-23
Many windows users assume an .iso file is a .zip file because Windows treats it wrongly as a zip file. To the op, I suggest using something like [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable sd card

---

### Post by rendell on 2015-05-23
cpu: i5 4200U
gpu: gt 720m
ram: 8gb
main os: win 8.1

That's why I'm asking why I can't find the .iso because I want burn it no my sd card.

---

### Post by rendell on 2015-05-23
I downloaded from here: [http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/) I download the 14.04 LTS one.

---

### Post by Vladlenin5000 on 2015-05-24
> **rendell said:**
> I downloaded from here: [http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/) I download the 14.04 LTS one.

If so you should have an ISO, nothing else. Needless to say, make sure you selected 64-bit ;)

---

### Post by rendell on 2015-05-24
I checked and realized that I have an iso file, the problem is that it is treated as a zip file.

---

### Post by Vladlenin5000 on 2015-05-24
> **rendell said:**
> I checked and realized that I have an iso file, the problem is that it is treated as a zip file.

It's a Windows "thing" as commented in post #4. I second the suggestion about Unetbootin. It's probably the easiest tool for you in Windows.

---

### Post by Bucky Ball on 2015-05-24
> **Vladlenin5000 said:**
> It's a Windows "thing" as commented in post #4. I second the suggestion about Unetbootin. It's probably the easiest tool for you in Windows.

+1. Carry on regardless and see what happens. If Win is simply mislabeling the iso a zip file, then hopefully Unetbootin won't be bothered what Win calls it and treat it as what it is ... an .iso. ;)

(PS: Thanks for the tip, cariboo. 'idiosyncrasy' noted.)

---

### Post by Mark Phelps on 2015-05-24
If you're trying to create the bootable USB in Windows, then consider using the Universal USB Installer.  I've used it multiple times to create bootable USB sticks from Linux ISO downloads.

---

