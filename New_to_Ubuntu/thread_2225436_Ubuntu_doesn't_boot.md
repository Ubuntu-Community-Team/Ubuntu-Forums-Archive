---
title: "Ubuntu doesn't boot"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by ritik2 on 2014-05-21
I tried to boot Ubuntu 14.04 using a USB. It seemed to be stuck on the splash screen forever. After several attempts, I decided to give it some more time. After about 50 minutes, it finally went past the splash screen but still didnt boot. I have attached a pic of the error that showed up. What should I do?

[ATTACH=CONFIG]253340[/ATTACH]

---

### Post by LastDino on 2014-05-21
We could benefit from more info, this however clearly says there are problems mounting the image.
System info, what usb manager you used to make this bootable and did you format the disk to fat or not before burning ISO on it?

---

### Post by ritik2 on 2014-05-21
PRocessor: AMD E1-2100 APU, Radeon HD Graphics 1GHz, 2 GB RAM, has Windows 8 pre-installed on it. I used Universal USB Installer to mount the image. Yes, I did format the USB.

---

### Post by hyperreal on 2014-05-22
I've had problems with Universal USB Installer, so I no longer use it.  I have found the Win32 Disk Imager to be the best program for making a boot USB.  [http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Win32-Disk-Imager.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Win32-Disk-Imager.shtml)

Run that program, select the Ubuntu ISO file, and press 'Write'.

---

### Post by ritik2 on 2014-05-22
It doesn't help though. I still get an error.

---

### Post by LastDino on 2014-05-22
Hmm unfortunately, I've no real way to approach this as hardware wise you seem fine, but to ask few more details;
Have you turned off secure boot?
Is that USB stick able to boot on some other machine with same ISO installed on it?
Is the ISO you burned on USB is x64 bit version?
Is checksum  checking out?

I would also suggest you to bring this thread in attention of Oldfred, he is extremely knowledgeable in these areas.

---

### Post by ritik2 on 2014-05-22
Ok, so I've successfully installed Ubuntu. I used a different boot manager and it did the work. But now, after installing it, I restarted my laptop, and well, I boot into Windows. This might seem like a silly question, but now how do I get to boot into Ubuntu?

---

### Post by LastDino on 2014-05-22
Which ''boot manager''? Or did you meant USB bootable tool?

Have you turned off secure boot? <That question is still valid.
Are you doing this in EFI or legacy mode?


Since you can boot into windows, can we see what partitioning scheme are you using?

---

### Post by whitesmith on 2014-05-22
As a courtesy to those helping you/ reading this thread, please used Thread Tools to mark the problem solved, if in fact it is. Cheers!

---

