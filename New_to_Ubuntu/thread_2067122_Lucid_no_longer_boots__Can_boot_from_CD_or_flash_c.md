---
title: "Lucid no longer boots / Can boot from CD or flash card either."
date: 2012-10-06
forum: New to Ubuntu
---

### Post by polaatx on 2012-10-06
Hello, 

I left my laptop running lucid on through the night while it was downloading a very large file. 

I the morning I found the laptop continuously rebooting over and over. Lucid no longer loads. 

I figured that the partition had filled. Once before I filled the partition and lucid no longer loaded. 

So I am trying to boot from CD in order to delete the very large file and free up space. But it won't load from CD. The Ubuntu blinking dots keep running for ever. 

The same happens when I tried to load from lucid on a flash card - which worked before. It keeps working literally for hours but lucid never loads. 

I tried to load GParted CD and again after a while the CD drive stops working and I get a blank black screen and sits there for ever. 

windows 7 is still working fine on a different partition. 

Can someone please give me some ideas on what could be wrong? why doesn't nothing loads anymore?

---

### Post by albandy on 2012-10-06
Try with SystemRescueCD
[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by polaatx on 2012-10-06
Hello, thanks for your reply. 

I put  SystemRescueCD on a flash card (using Windows USB installer) but again nothing loads. I just get a blank black screen with a cursor blinking for ever. 

**It seems something is preventing the laptop from booting from CD or USB. **

Windows 7, which is on a separate partition than Lucid, still boots fine. 

Any ideas on what could be causing this?

---

### Post by polaatx on 2012-10-06
Hello, In case this is a video issue, I tried setting NOMODESET as explained here [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132") but it didn't help. Again, while booting from Lucid CD or USB key, the ubuntu logo with the 5 blinking white/red dots just keeps running for ever.

---

### Post by MoebusNet on 2012-10-07
Allow me to share an experience I had recently with my laptop:

I was getting corrupted CD's when burning them and the notebook wouldn't boot from the CD. This notebook has a removable CD/DVD drive, so I wound up removing and reinstalling  the same CD/DVD drive. That improved the connection enough to solve my problems with data corruption. Could this be a problem for you?

Also, are you sure you're booting from the CD or USB key, not the HDD? Elementary I know, but have you checked your BIOS setting to make sure you are booting from the CD/USB? In the past I have unplugged the power to a HDD just to make sure I was booting from CD/DVD/USB.

Just brainstormin', you've probably thought of all this but it's free to ask right?

---

### Post by polaatx on 2012-10-07
Hi MoebusNet, thanks for your response. Yes, I set the bios to boot from USB. When the external USB CD player/recorder is plugged in, it boots from that. Otherwise, it boots from the Flash card inserted in the card reader. 

Both CD and the flash card have been used before to install/modify the Lucid currently installed on this laptop and also install it on other machines, so I don't think it is likely that both have been corrupted. Also it doesn't boot from SystemRestoreCD installed on another flash card. 

In short, the machine has lost the ability to boot into lucid on hdd and ANY USB device. 

S**o does that mean problem is with Grub? **

As stated before, windows 7 (installed on a separate partition on HDD after Lucid) still boots fine.

---

### Post by Wim Sturkenboom on 2012-10-07
No, this does not sound like grub. USB/CD boot (attempts) come before grub (on HD) is started; as the former already fail, it's not a grub issue. And you can boot windows which implies that at least the grub files in the Linux partition are still fine (if you're using grub as the boot loader).

I would try to 'reset the bios' as a possible solution.

---

### Post by MoebusNet on 2012-10-07
Just out of curiosity, are you able to run the checks for RAM and the check for errors on the Live-CD or Live-USB drive?

---

