---
title: "Dual boot problems"
date: 2022-09-06
forum: New to Ubuntu
---

### Post by stcfthots on 2022-09-06
Hi 

So I'm trying to install Ubuntu for the first time on my laptop. I've shrunk my windows C drive by 150gb to create some free space, disabled BitLocker and also disabled secure boot. The Ubuntu iso file is on external HDD which was formatted to FAT32. 

I seem to be unable to launch the installation file for Ubuntu. I selected the correct drive using my BIOS menu and I'm able to choose the install Ubuntu option. However the screen then goes into a loading cycle. When I press f6 I can see a log of what's happening and in particular I keep receiving the following messages over and over again:

[FAILED] Failed to start Network Name Resolution
See 'systemctl status systemd-resolved.service' for details 

[FAILED] Failed to start Userspace Out-of-Memory (OOM) Killer
See 'systemctl status systemd-resolved.service' for details 

[FAILED] Failed to start Network Time Synchronisation
See 'systemctl status systemd-resolved.service' for details 

Any idea on how to fix this? I was hoping to start my coding journey but I cannot even install Ubuntu to begin with haha!

Thanks in advance

---

### Post by tea for one on 2022-09-06
Assuming your ISO is OK and the utility used to create the install media are sound, I would first use the option [COLOR="#0000FF"]Try Ubuntu[/COLOR] rather than [COLOR="#0000FF"]Install Ubuntu[/COLOR].
Sometimes (although very rare) internet connection prevents clean installation.

---

### Post by stcfthots on 2022-09-06
Hi I do not have such option. The last selection I make is "Try or Install Ubuntu" then the screen goes into a loading stage

---

### Post by stcfthots on 2022-09-06
Hi 

I've also tried doing this with and without the ethernet cable plugged in so I doubt the internet has any interference with it

---

### Post by tea for one on 2022-09-06
Try a different USB port?
Or a different USB device?

Further info here [https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot](https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot)

Also, it may help to supply the PC specification.

---

### Post by stcfthots on 2022-09-06
Hi 

I've looked at your lists of suggestions and decided to use the virtual machine method instead :) 

I'm trying to install Ubuntu and have gone down the "something else" route in order to keep all of my windows files however the install now button is greyed out? 




[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290998&stc=1[/IMG]

---

### Post by col48 on 2022-09-06
Maybe this is a BIOS/UEFI issue?  I think the partitioning prerequisites are different.

---

### Post by Dennis N on 2022-09-06
> I'm trying to install Ubuntu and have gone down the "something else" route in order to keep all of my windows files however the install now button is greyed out?
In your image, you have a disk (sda) but no partition table or partitions. You need a partition to install to.

---

