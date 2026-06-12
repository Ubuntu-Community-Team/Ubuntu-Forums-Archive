---
title: "&quot;No Operating System Found&quot; after installing Ubuntu 14.04 LTS on HP PV 21"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by jesc892 on 2014-07-26
Hello, I recently purchased an HP Pavilion 21 All in one pc that came preinstalled with windows 8.1.
Since I really enjoy the ubuntu environment I decided to replace windows 8 with ubuntu. I created a Live USB and everything seemed to install fine. 
After I get the notification to reboot, I go ahead and do that. Now this is where the problem occurs. I get a new boot option called 'ubuntu' which I am assuming is the newly installed ubuntu OS.
I set that option to boot first, but unfortunately I get an error saying No Operating System Found. I searched online and it seems to be a problem with the MBR. I'm guessing
due to the UEFI, it got placed in an incorrect path. I did a Boot Repair but it did not fix my problem. 
I did get a URL that I'm sure someone with greater knowledge than me can help me find the root cause of the problem and fix it accordingly.
[http://paste.ubuntu.com/7867767/](http://paste.ubuntu.com/7867767/)

Please somebody help me with this, I don't want to give up on Ubuntu yet!

---

### Post by whitesmith on 2014-07-26
Linux will only boot from an ext2 - ext4 parftition. That would be sdb2 in your case. This should be the bootable partition. While you're at it it, make the partition ext4.

---

### Post by mooreted on 2014-07-26
This looks like a pretty good source:

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by jesc892 on 2014-07-26
> **whitesmith said:**
> Linux will only boot from an ext2 - ext4 parftition. That would be sdb2 in your case. This should be the bootable partition. While you're at it it, make the partition ext4.

I am guessing I can use GParted to change this? According to GParted I have boot flags in sda1 and sdb1. 
Should I move the boot flag to sdb2? And what about the other boot flag in sda1?
And when you say change the partition ext4, which one are you refering to? It seems that sdb2 is already ext4.
Sorry if I am asking too many questions, I don't have much knowledge on partitions...:|

---

### Post by jesc892 on 2014-07-26
> **mooreted said:**
> This looks like a pretty good source:

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

It seems that this is more focused on dual booting, where as I replaced windows with ubuntu entirely.
Thanks for the link tho!

---

### Post by whitesmith on 2014-07-26
> **jesc892 said:**
> I am guessing I can use GParted to change this? According to GParted I have boot flags in sda1 and sdb1. 
Should I move the boot flag to sdb2? And what about the other boot flag in sda1?
And when you say change the partition ext4, which one are you refering to? It seems that sdb2 is already ext4.
Sorry if I am asking too many questions, I don't have much knowledge on partitions...:|

According to the Boot Info Summary, only sdb2 has a boot sector type that Linux recognizes for executable programs. It can read and write the others, but not operate from them. Distinctions like this will become less abstruse as your knowledge of the OS grows. Look at it this way: Linux can read and write on Windows partition types (FAT, FAT32, NTFS), but it can **not** run on any of them. Does this make sense?

---

### Post by jesc892 on 2014-07-26
I understand that Linux needs to be on ext4 and sdb2 has that type, but how do I go about changing that? I don't want to mess up my pc any further than I have already. I'm not sure what tools I will need to accomplish this. So far from what I read online I can do this with gparted...or via the terminal but I'm not 100% sure the steps I need to do this and I know that if I make a mistake here I'll just be digging a deeper hole :(

---

### Post by mooreted on 2014-07-26
Rather than messing around with Grub and trying to get a boot loader configured on one of the partitions, it might be easier to re-install Ubuntu. When you get to the partitioning part of the install choose, "Use the entire disk".

Because of UEFI, make sure you install the 64-bit version of Ubuntu.

---

### Post by mooreted on 2014-07-26
> **jesc892 said:**
> I am guessing I can use GParted to change this? According to GParted I have boot flags in sda1 and sdb1. 
Should I move the boot flag to sdb2? And what about the other boot flag in sda1?
And when you say change the partition ext4, which one are you refering to? It seems that sdb2 is already ext4.
Sorry if I am asking too many questions, I don't have much knowledge on partitions...:|

It's more complicated than changing the boot flag. You have a boot loader called Grub that needs to know where the root file system is so that it can find the kernel and boot the rest of the operating system. Believe me, you don't want to get into configuring Grub right now.

---

### Post by jesc892 on 2014-07-27
I downloaded the 64-bit Ubuntu so I know that's not the problem. I have also been repeatedly reinstalling Ubuntu using the option 'Erase disk and install Ubuntu'. Every time I get the same error. I'm starting to think I'm not going to get very far in resolving this without changing the grub, which I totally have no confidence in doing :/

---

### Post by mooreted on 2014-07-27
I suppose you could boot up to the live session, and when you get to the partitioning section of the install you could choose manual partitioning. You would then delete all the partitions, create a swap partition if say 512MB and a root partition on the rest of the unused space.

When I do it this way, I have found it's often best to delete all partitions on the drive then reboot and continue partitioning after a reboot.

If you have more than one physical drive and you are not setting up a RAID, I have found it's easier to disconnect all but the drive I want to install Linux on. Sometimes the partitioning tool is too helpful and wants to find all your drives for you.

---

### Post by jesc892 on 2014-07-27
Well I figured out how to fix the problem. What I did was first I went into my BIOS and enabled Legacy mode on. Then I loaded ubuntu from the usb and reinstalled, and when I restarted I choose the hard drive that the boot was located in and it booted correctly. So basically it was as simple as turning on legacy mode in the bios and then finding out which boot option under the legacy mode to boot up. Thanks to everybody who attempted to help and gave their input! I can now fully enjoy ubuntu once again \\:D/

---

### Post by mooreted on 2014-07-27
Stupid UEFI, I hate it.

Good job figuring it out. Hopefully you can now relax and enjoy Ubuntu.

---

### Post by whitesmith on 2014-07-27
Have you tried the simplest option, booting from the original Ubuntu media and using the "Try" option? That's usually the best way to see if Ubuntu is compatible with your hardware. Let us know.

---

### Post by tagy011 on 2014-07-28
OK  , since you are coming from win. 8.1 , new machines that now come with win. 8.1 are installed under UEFI / EFI , instead of legacy mode . Most likely what happened in your case is that ubuntu was installed in legacy and you are booting up in UEFI and that will give you the error no OS installed . Go to BIOS and switch to legacy and your ubuntu will boot up . To install 14.04 in UEFI , which is the only version that supports UEFI follow this link [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) . If it is too complicated for you stick with Legacy mode . UEFI / EFI is the new BIOS firmware with new features such as secure boot and others .

---

