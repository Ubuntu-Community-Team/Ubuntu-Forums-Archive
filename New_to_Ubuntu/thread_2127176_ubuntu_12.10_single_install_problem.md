---
title: "ubuntu 12.10 single install problem"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by okkie on 2013-03-19
I am trying to  single install 12.10 on a formatted disk.
Computer used to be XP.
sometimes the screen says 'HD does not support HDA' and stops.
Other times it goes on trying to boot but under 'boot from cd' it says NTLDR missing and
control+alt+del to restart which simply starts the process all over.
Can someone please tell me what to do.

---

### Post by grahammechanical on 2013-03-19
This
> [COLOR=#000000] 'boot from cd' it says NTLDR missing[/COLOR]
is apparently a Microsoft error message.

[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)

I guess that you are using some kind of BIOS or even a Windows boot manager to try to load the Ubuntu DVD and the boot manager is looking for certain Windows files which are not there and cannot be there because the Ubuntu DVD is not a Microsoft Windows DVD.

Enter the BIOS and change the boot priority to boot from CD/DVD before booting from the Hard Disk. That should point the BIOS to the Ubuntu DVD when looking for an operating system.

Regards.

---

### Post by okkie on 2013-03-20
Thank you for your assistance.
I now got it to read the CD. It goes to the UBUNTU purple screen with the dots and then to the [initramfs] commandline which says 'unable to find a medium containing a live file system' . If I put 'help' into the command line it gives a lot of commands but with my knowledge I am stuck.
If my install CD is not containing a 'live' Ubuntu system, please tell me where I can download one. Thks

---

### Post by c2tarun on 2013-03-20
> **okkie said:**
> Thank you for your assistance.
I now got it to read the CD. It goes to the UBUNTU purple screen with the dots and then to the [initramfs] commandline which says 'unable to find a medium containing a live file system' . If I put 'help' into the command line it gives a lot of commands but with my knowledge I am stuck.
If my install CD is not containing a 'live' Ubuntu system, please tell me where I can download one. Thks

It'll be really helpful for us to help you if you share your method of creating live CD for ubuntu. I guess you used "make disk bootable" option of Nero.
Meanwhile you can crosscheck you method from [this]("https://help.ubuntu.com/community/LiveCD#Preparing_your_LiveCD") link.

---

### Post by squakie on 2013-03-20
+1.  You can't create a bootable disk then just copy the downloaded ISO of Ubuntu to it.  You instead need a fresh DVD (the new images won't fit on a CD anymore), the ISO you downloaded, a burner program and then BURN AN IMAGE and select the ISO.

---

### Post by okkie on 2013-03-20
I downloaded 3 12.10 ISO's from the official site.
I now also have a usb stick prepared.
I can now boot into Ubuntu pink/purple screen with the moving dots which then produces '[INITRAMFS]unable to find a medium containing a live system.
how did it get to the purple screen if not reading the cd in the rom ?
Unitramfs is a command line. Which command does it want ?
I used a windows machine to format the hard disk I now want to install Ubuntu onto. Is that good enough ?

---

### Post by Impavidus on 2013-03-20
It clearly boots, giving the screen with the dots, but it gets stuck. Can you give us the specs of your computer? I'm particularly interested in the amount of RAM. I suspect it can load the live OS but is unable to create a live file system in RAM.

---

### Post by okkie on 2013-03-21
Thanks for the assistance,it looks like we are now going in the right direction.
I know little about ram. I have over 500 memory and can take that to over i000.
Are they related and how can I determine the state of my ram?

---

### Post by okkie on 2013-03-21
I also note at start up that memory runs at dual channel. I have'nt seen that before

---

### Post by ManamiVixen on 2013-03-21
512MB is too little for Ubuntu 12.10. I wont boot on that. If your PC has 512MB of ram, you are better off with Xubuntu or Lubuntu 12.10, OR Ubuntu 12.04 installed via alternate and you use the Unity 2D interface as the 3D might be slow for you on your PC.

---

### Post by okkie on 2013-03-21
I have now increased the memory to 2097152k

---

### Post by okkie on 2013-03-22
my problem not receiving attention anymore.May I start a new thread ?

---

### Post by Impavidus on 2013-03-22
You wrote you added some RAM to your machine, which in itself won't trigger much response from the forum members. So, can you now boot the live system or not? If not, does it still give you the same error message? Is your memory recognised?

---

### Post by okkie on 2013-03-22
thanks for coming back.
I now managed to do a complete install of 12.10 and right at the end it tells you to restart the computer.
In stead of restarting/booting it opened a  dark screen with two red dots right in the middle and a checklist from the top left down 'starting and stopping various processes' with two failures, 1 and 7 as follows

starting save sound card mixer state...................fail
starting set console font.....................................fail
All others...........................................................ok
I have'nt touched a thing since and  don't know what to do

---

