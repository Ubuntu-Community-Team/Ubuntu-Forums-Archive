---
title: "Boot-Repair not working. Having a hard time booting Ubuntu"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by Light Knight 22 on 2013-05-11
Hello everyone. 

Ok, I attempted a fresh Ubuntu install as I was having some internal system errors. When a simple "re-installation" didn't fix anything, I performed a "delete Ubuntu 13.04 and reinstall" from the boot USB. 

That's when it all began. First I had a grub problem, where all I got at boot was the Grub Recovery. So I booted my windows recovery and repaired it. Now I can boot into to windows only.

So I installed Ubuntu again but still no dual boot choice, it goes right to windows. So I've just ran Boot-Repair, following these steps: [http://askubuntu.com/questions/142750/after-installing-ubuntu-from-usb-grub2-cant-be-installed/142751#142751](http://askubuntu.com/questions/142750/after-installing-ubuntu-from-usb-grub2-cant-be-installed/142751#142751) .

When I try runing Boot-Repair, I get this message at the end:
> Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 13.04 (sda6). Then try again.

Please help, as it has been several days of frustration getting into my Ubuntu partition.

---

### Post by Impavidus on 2013-05-11
Which windows version is this? And, as you already found boot repair, can you post a link to a boot info summary?

---

### Post by Light Knight 22 on 2013-05-11
[http://paste.ubuntu.com/5654973/](http://paste.ubuntu.com/5654973/) is the log I just ran. And I run Window 7 64 bit.

---

### Post by oldfred on 2013-05-11
This is a new error message, usually the top part of bootinfoscript shows the grub in the Windows install.
> 
GRUB detected inside Windows partition. Rename /mnt/boot-sav/sda1/grub into grub_old

You have to install grub to the MBR to be able to multiple boot. Is the issue of not having a repository, because Internet is not working? You need Boot-Repair to install grub to the MBR.

It also looks like you booted Boot-Repair in UEFI mode. Your install is BIOS and need to be consistent with which mode you are in.

---

### Post by Light Knight 22 on 2013-05-11
Hi, thanks for your reply. I checked, and all this time I have been running the USB in UEFI mode. That includes all the times I re-installed. 

The internet works fine (I am using it to reply right now). Here is the log from the Boot-Repair in BIOS. [http://paste.ubuntu.com/5655865/](http://paste.ubuntu.com/5655865/) 

This may be totally off: but now that it is running in BIOS, if I try installing Ubuntu, there is no "reinstall option at the first screen. So I click "something else" that brings me to the partition editor. Should I attempt to set the ubuntu mount point to / and reinstall that way? I was about to try, but when I edit the ubuntu partition, there is a drop down list where the default selected is "do not use this partition". I'm not sure what to do here.

---

### Post by oldfred on 2013-05-11
Your install actually looks ok, but you do not have grub in the MBR of sda. If you run Boot-Repair does not not now install grub?

I think the manual install just defaults ot do not use, but do not remember.
Normally if partition exists and you want to reinstall, you click on change, use as ext4, check format box, and mount as / (root). If you have swap it should find it.
Combo box at bottom of install screen should show sda as default for install of grub2 boot loader. That should be fine.

---

### Post by Bartender on 2013-05-11
> **Light Knight 22 said:**
> So I click "something else" that brings me to the partition editor. Should I attempt to set the ubuntu mount point to / and reinstall that way? I was about to try, but when I edit the ubuntu partition, there is a drop down list where the default selected is "do not use this partition". I'm not sure what to do here.

Don't let that "do not use this partition" throw you off.  That's been the default choice forever.  I don't know why.  It is a little confusing the first time.  Just click on it (or next to it?) and you'll get a drop-down with a bunch of choices.  You are correct; "/" is the choice for the operating system.  If I'm manually installing I almost always set 20 to 25 GB for /, then create an extended partition, then within that extended partition create a several GB logical swap partition.  Then one more logical partition for /home, using up whatever's left.

---

### Post by Light Knight 22 on 2013-05-12
I thought I only need the two partitions. One EXT4 and one swap?

The partitions are already all allocated, as I have run Ubuntu for over a year on it. I'm trying to re-install. You suggest I still make one / partition, one swap, and one /home? 

Also, when I am making up my partitions, the Windows 7 partition is default set to "do not use this partition", will this create a problem with windows?

---

### Post by oldfred on 2013-05-12
If you click on the Windows partition to use it then it gets overwritten, you want to change to another partition.

---

### Post by Light Knight 22 on 2013-05-17
Hello again.

It works! I was able to reinstall ubuntu if I booted the usb in bios.

Last question before I mark it at solved: I now have a Windows loader on sda1 and sda2. Does it matter which I load?

---

### Post by oldfred on 2013-05-17
Not really. Windows normally installs to two partitions. A small 100MB boot/repair partition that f8 will also give you a repair console. Boot-Repair probably copied the boot files into the main install as backup, but then grub2's os-prober finds both sets of boot files. And from grub's menu f8 is just about impossible to use as grub to Windows is so quick. Some say it may work if you try many times and are quick enough. But just better to make a Windows repairCD anyway.

---

### Post by Light Knight 22 on 2013-05-18
Thanks oldred and bartender! I seem to be having an other problem with the repositories, but I think it's better I make a seperate thread.

---

