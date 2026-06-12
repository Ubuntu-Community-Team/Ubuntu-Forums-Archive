---
title: "multiboot question"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by s1wood on 2012-05-08
I would like to install windows XP alongside my Ubuntu OS - I need windows for a couple of things and I have plenty of disk space but not enough memory for VirtualBox to run well. 

I have read up the advice on installing XP after Linux and the bit that frightens me off is reinstalling Grub, I have had a lot of problems with Grub in the past which is OK when I was playing with a spare computer but I daren't risk my main system.

What I was wondering was whether, if I installed XP on a partition and then installed a lightweight Linux after that, whether the new Linux OS would provide a bootloader for both XP & Ubuntu  - just a thought, any idea if it would work?

Susan

---

### Post by oldfred on 2012-05-08
It is not really difficult to reinstall the grub2 boot loader to the MBR and run sudo update-grub to find a new Windows install and let you boot both.

You do need to have a current version Ubuntu liveCD or USB to boot from and run repairs.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

It can as simple as two lines if you know your root partition, if separate /boot partition you also have to mount that:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=DarkRed]sudo mount /dev/sda5 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
[COLOR=DarkRed]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Windows will only install in a primary (sda1 thru sda4) NTFS formated partition with the boot flag, or unallocated space with a primary partition available. It does not see the Linux partitions.

It does not hurt to have a repair CD or more:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Curtis6767 on 2012-05-08
According to their homepage,[ EasyBCD]("http://neosmart.net/EasyBCD/") is supposed to make multi-boots a bit easier.

I can not vouch for it as I have not used it, but it might be worth exploring. It is free for non-commercial users. Just click on "See Plans."

---

### Post by wilee-nilee on 2012-05-08
+1 to post 2.

---

### Post by oldfred on 2012-05-08
EasyBCD is for Windows 7 or Vista as they have BCDs. 

Windows XP does not have a BCD but uses boot.ini. A few here have used EasyBCD with Windows 7, but primarily those with Windows DRM restricted software that writes some of the digital rights serial numbers info into hidden area that grub2 also uses. EasyBCD eliminates that conflict but makes grub2 less reliable for booting Ubuntu.

---

### Post by s1wood on 2012-05-09
>It can as simple as two lines if you know your root partition, if separate /boot partition you also have to mount that:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=DarkRed]sudo mount /dev/sda5 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
[COLOR=DarkRed]sudo grub-install --boot-directory=/mnt/boot /dev/sda<

[COLOR=Black]Nothing there looks simple! 

Looking at disk utility, I currently have 
boot sda1
root sda2
swap sda5
home sda6
then the currently unallocated space I would put XP on

So how do I install MBR from a live CD?
What commands would I then run?

Just a thought - what would happen if I just re-installed Ubuntu (keeping home) after installing XP - would that sort the bootloader for me?

Susan

[/COLOR][/COLOR]

---

### Post by oldfred on 2012-05-09
Reinstall will work, I normally do not suggest a separate /boot partition for most desktops. Servers, or installs with RAID, LVM or some of the other formats may need a separate /boot. 

Otherwise you need three lines to reinstall grub and a lot of the instructions do not include that as it is not common.

#If separate /boot & Natty or later
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by s1wood on 2012-05-09
Thank you for that advice, I shall try it out when I am ready, I've bookmarked the page on my netbook.

I installed a separate boot partition on the instructions somewhere  on the Ubuntu site - is this out of date or was it never necessary?

Susan

---

### Post by oldfred on 2012-05-09
Generally old instructions, not from Ubuntu. Ubuntu's standard auto install is just / (root) and swap.

But some very old computers have a BIOS limit of 137GB. Either the entire / (root) or a separate /boot have to be entirely in the first 137GB. This applies more for those with old computers originally with 120GB drives or less and upgrade to a much larger drive.

Also some with very large over 500GB drives have had boot issues when they create just a / & swap for the entire drive. I think it is a BIOS setting but never have found a user who could prove it. Most resolve that issue by creating a much smaller / and use the rest of the drive as /home or other data partitions.

---

### Post by s1wood on 2012-05-09
Thank you for the information.

Susan

---

