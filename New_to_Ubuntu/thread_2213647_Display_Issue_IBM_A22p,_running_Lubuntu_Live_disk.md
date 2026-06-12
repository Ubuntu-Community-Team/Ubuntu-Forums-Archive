---
title: "Display Issue IBM A22p, running Lubuntu Live disk"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by lou7 on 2014-03-27
It starts up from the live CD, but the display is screwed up. split in 3 sections,2 vertical lines split and duplicate the display. I can barely navigate moving the apps in between LCD enough to run.

I've read it's obviously a video driver issue. I just do not know where to start?

I'm able to use File Manager, is there a file I can modify?

Ibm thinkpad A22p type 2629:
   Graphics ProcessorAGP 2x - ATI RAGE Mobility 128 - 16 MB SGRAM
   Supported Display Graphics XGA (1024x768)

I know windows and have very little Ubuntu experience, but I'm trying to get with the program. I just need a little jump start to get going.

---

### Post by lou7 on 2014-03-29
I can now run it from the LXDE Lubuntu live CD in safe graphics mode (low graphic default 800X600 resolution). My problem will be when I try and do an install to my hard drive, it will not like the ATI RAGE Mobility 128 hardware. I want to fix it while I'm still able to do something. 

Any help here?

---

### Post by mörgæs on 2014-03-29
You are really pushing the limits with such old hardware. I suggest you use the [alternate Lubuntu ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"), not the standard live ISO. Remember to have wired internet access during the install.

---

### Post by lou7 on 2014-03-29
Thank you for your reply,

I understand the limitation on the Laptop, actually for me it runs pretty good as the live CD option and I like the LXDE options. I will give the alternative ISO a shot.

---

### Post by lou7 on 2014-03-29
I haven't tried the alternative ISO yet But:

Re-attempted to run Regular Live CD and failed at the X server (Your Graphical Interface). It did however allow me to make changes (via some terminal pop out, had to use "root" as the password, I guessed at it), the video setting yes something like ~mach128 to I changed it to something like~ATI 128 and it came up in the Regular live CD now. Hope to try an install to hard Drive next.

---

### Post by lou7 on 2014-03-29
Ok while in the LXDE Live CD, I did the install PCOSlinux Installation wizard it appeared to be successful, when done selected a shutdown. The screen went black but the pc never shutdown. I ended up pushing power button. Next turned laptop back on, removed CD, it goes directly right into my windows xp startup screen. I did not see a Grub screen.

---

### Post by lou7 on 2014-03-29
Re installed again, followed all the instructions, after reboot goes right back into Windows again, WTF! Does anything go easy with Linux!

---

### Post by DogMatix on 2014-03-29
Does pressing <shift> key during start-up bring up the GRUB screen?

---

### Post by lou7 on 2014-03-30
No Go, I tried a bunch of times. Still goes into Win startup.

---

### Post by lou7 on 2014-03-30
Just tried running Boot Repair Disk another fiasco! WTF!

tells me to copy or type three lines:

first line: sudo chroot "mnt/boot-sav/sdb1" dpkg --configure -a

response is no such file or directory.

Paying for Windows 8 isn't looking so bad right now.

---

### Post by mörgæs on 2014-03-30
Posting in another tone might attract more people to your thead.

Signing off.

---

