---
title: "&quot;Operating system not found&quot; IBM Thinkpad R50."
date: 2012-06-12
forum: New to Ubuntu
---

### Post by KudoT on 2012-06-12
I'm trying to install Xubuntu on my Thinkpad R50.
It installs fine from what I can tell, but it just won't boot into it, it gives me the "Operating system not found" screen.

I've been talking to another community (4chan /g/), they pointed me in the direction that my drive might not be set as bootable, so I went through the steps and now have my /dev/sda1 set to bootable as indicated by the "*" in fdisk through terminal using the live CD "try Xubuntu".

However, it still tells me "Operating system not found".
I've tried reinstalling at least 15 times, every time it ends up on the same screen.

In my latest attempt I've let the installer do the partitioning, I'm currently sitting on the Live CD preview eagerly awaiting your replies.

Some more details:
-I'm selecting boot from HDD through the Thinkpad's BIOS.
-As soon as I get past the IBM splash screen it goes to OS not found
- I have not even seen this "GRUB" screen.
-I've pulled out 60% of my hair.
-I am completely new to GNU/Linux (probably obvious, seeing as I'm having trouble installing a Ubuntu based distro.)

Any and all help is greatly appreciated, Please respond, and thanks in advance.

---

### Post by arochester on 2012-06-12
Have you checked the BIOS to see what boots in what order?

Does the LiveCD work in a different machine?

---

### Post by mapes12 on 2012-06-12
As the previous PO has mentioned, if you are in control of booting from your CD/DVD drive then you have loads of options. If I had your problem then I would take the drive back to its factory gate state by running **Kill Disk**(Google for latest version, it's free) over it. Then start again.

EDIT - Just looked on the Killdisk site and they make reference to DOS and Windows. I have found this irrelevant. Just run it across your HDD and you will have a clean disk to start again.

---

### Post by oldfred on 2012-06-12
From Ubuntu liveCD or download a full liveCD run the Boot Info from this. It may also repair a system, but we should review where you are at to make best suggestion.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by KudoT on 2012-06-12
> **arochester said:**
> Have you checked the BIOS to see what boots in what order?
Yes, The boot priority is exactly how it should be, the drive is marked as bootable and the OS didn't appear to have any problems installing.
I'm sure the live CD will work in another system, I'll test it out now to confirm.

EDIT: The live CD works fine In another system just like the thinkpad. 

> 
From Ubuntu liveCD or download a full liveCD run the Boot Info from  this. It may also repair a system, but we should review where you are at  to make best suggestion.
I'll give this a try from the Live CD shortly, and try Killdisk lastly if that doesn't work.

Thanks for the replies.

---

### Post by mastablasta on 2012-06-13
this kind of message could happen if master boot record of the disk is corrupted. did this laptop had any viruses or rootkits on it before?

---

### Post by KudoT on 2012-06-13
> **mastablasta said:**
> this kind of message could happen if master boot record of the disk is corrupted. did this laptop had any viruses or rootkits on it before?

No idea, It used to boot into it's XP install fine before it was removed, I was given this laptop by a freind who was rather tech illiterate however so maybe it does? If so, should I just killdisc? (still waiting to do a boot-repair, it likes to not connect to the internet sometimes, so I have to wait before I can try.)

---

### Post by mastablasta on 2012-06-13
well the no operating system is show when computer BIOS can't find the operating system. meaning somehting is wrong with disk. for example the disk is not present, the disk is faulty, the cable to the disk is faulty or unplugged, master boot record is corrupted.
 
if you suspect that it's a software error (and that hardware is ok) and sinc eoyu can boot using live media i would suggets you run this script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
it was made by a forum member to help others troubleshoot boot issues. so follow the instructions found on the site and post the results here in forums. it could be that there is an easy fix. hard to say. but the script will show how boot is cofigured.

---

### Post by KudoT on 2012-06-13
> **mastablasta said:**
> if you suspect that it's a software error (and that hardware is ok) and sinc eoyu can boot using live media i would suggets you run this script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I've run the script here's a paste of the results:
[]("http://pastebin.com/zPTcVUe8")[http://pastebin.com/zPTcVUe8](http://pastebin.com/zPTcVUe8)

---

### Post by oldfred on 2012-06-13
Your 8GB flash drive has no boot loader in the MBR, but sda looks normal and should boot. Do you have BIOS set to boot hard drive first? And/or remove flash and see what happens.

---

### Post by KudoT on 2012-06-13
> **oldfred said:**
> Your 8GB flash drive has no boot loader in the MBR, but sda looks normal and should boot. Do you have BIOS set to boot hard drive first? And/or remove flash and see what happens.

The flash drive was only in the computer so I could run the script, It's usually disconnected.
The boot order is also fine ( HDD > CD > Removable).

The CD drive on the Thinkpad isn't 100% to my knowledge, I had to clean the lens for it to read the disc as it hadn't seen use in quite a long time, think that would have anything to do with this problem or would the script have told us about that? If so, I could try installing Xubuntu onto a portable HDD/USB and booting it through the Thinkpad to see if this is an issue..

I'm really grasping at straws here.

---

### Post by oldfred on 2012-06-13
the script only shows that all the pieces are there. If they were corrupt in some way, they usually would not install correctly, but I suppose if a bit was dropped in the middle of a file that could cause major issues.

Is USB flash a bootable choice on your system? If so you could install from flash drive.

---

### Post by KudoT on 2012-06-13
I can boot from USB yes, but when I make a live USB from unetbootin the installer says it cannot find the .iso/image file or something along those lines.

---

### Post by oldfred on 2012-06-13
I think most find unetbootin works, but you can try the pendrive one also.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by mastablasta on 2012-06-14
> **KudoT said:**
> I can boot from USB yes, but when I make a live USB from unetbootin the installer says it cannot find the .iso/image file or something along those lines.
 
 
you can select the iso manually in unetbootin. don't select the OS, just select the ISO.
 
If iso is good it will proceed to "burn" the live image to USB. 
 
If you are using windows a good interface is LinuxliveUSB

---

### Post by jtarin on 2012-06-14
Run the installation and install to your USB. Then boot with USB to check. Grub to USB.

---

