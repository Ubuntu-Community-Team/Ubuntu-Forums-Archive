---
title: "Fresh Install on SSD -- Can't see 'System Drive' in Home Folder"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by jimafternoon on 2013-04-08
I replaced my HDD with an SSD today and did a fresh install from usb. At first, I just chose the 'Install Ubuntu' option, but it wouldn't boot, all I got was a black screen. So, I tried again using the "Something Else' option.  After playing around with that, I finally got it to boot. But where I used to see "System Drive" in the folder view, there's nothing. If I plug in a thumb drive, it will show up. 

I'm thinking maybe I screwed up the partitions when installing, here's what I ended up with (I really had no idea what size to make them, so maybe somebody can comment?)

[IMG]http://i.imgur.com/zgmP1Ce.png[/IMG]
Thanks for any help!

---

### Post by oldfred on 2013-04-09
Is this a new system? That has UEFI or BIOS/legacy/CSM as boot options?
The efi partition is usually mean you booted with UEFI.

System drive is normally the main Windows partition, you have sda1 / (root) and sda3 swap with the sda2 efi boot partition. Normally the efi partition is 200 or 300MB and first. The root partition works a bit better if 20 to 25GB and the rest of the drive as /home or just data partition(s). Nothing really wrong with the partitions you have other than efi is very large.

---

### Post by jimafternoon on 2013-04-09
Ok, thanks. 

Is it too late to shrink down the efi?

I don't think I have UEFI or legacy. This computer is slightly less than a year old and came with windows 7, the UEFI thing came after I believe, if I understand correctly that it was the thing that initally prevented users from using any OS but windows 8 until a workaround was found?

I used the efi partition because the installer gave me prompt about it, and it didn't work when I ignored it the first couple of times I tried.

---

### Post by oldfred on 2013-04-09
Since it shows mounted at /boot/efi, I am pretty sure you have UEFI. You can shrink it at any time, but usually it is the first (or second) partition as that is the UEFI recommendation. I thought that requirement might be that the UEFI FAT driver might not be able to read files far into a larger drive, but if yours works then it must be ok.

Some of the first generation Intel i-series system's motherboards had UEFI and most of the second generation did. But Windows was usually installed in BIOS/Legacy/CSM or compatibility mode. 
Some Windows 7 systems within the year before Windows 8 were installed in UEFI, but did not have secure boot. Windows 8 on pre-installed systems are all UEFI with secure boot. 

How you boot installer either UEFI mode or BIOS mode is how it installs.
The Ubuntu installer will normally only install in UEFI mode to blank drives or drives that already are partitioned gpt. If drive was already MBR(msdos) then it would install in BIOS mode. UEFI only works on gpt partitioned drives.

---

### Post by jimafternoon on 2013-04-09
Ok. Well, I'm not sure that it is working right. Sometimes when I try to boot it goes to a black screen and nothing happens, and I have to retry it until it boots up. 

I ran the 'Boot Repair' tools and it told me that my efi was probably too far away from the beginning of the 'disk' to boot properly. 

So if I start over, what would be the best scheme for creating the partitions form the 'Something Else' option in the usb installer?

I will try and find out about the uefi.

---

### Post by jimafternoon on 2013-04-09
Ok, I think it might not be a boot problem, but a graphics card issue. I just restarted my machine and got the black screen again as it tried to boot, and this popped up:

"The system is running in low graphics mode -- your screen grpahics card and input device settings could not be detected correctly, you will need to configure these yourself" 

After a few tries I got it to boot up, but my switchable graphics were acting up again. I found a script to disable switchable graphics at startup, but this time it ddin't work and I had to do it manually (my fans runs constantly and the machine runs hot if its not disabled)

The solution I found to disable it at startup called for placing the three 'echo' lines in --> gksudo gedit /etc/rc.local.  I also added the fstrim -v / and another ssd option yesterday in the same place. 

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
fstrim -v /
#
# Modification for SSD
for dir in apparmor apt cups dist-upgrade fsck gdm installer samba unattended-upgrades ;
do
           if [ ! -e /var/log/$dir ] ; then
                   mkdir /var/log/$dir
           fi
done
exit 0
```

Anyway, the black screen at bootup might be a graphics issue related to the ongoing apport-gpu errors I've been having.

---

### Post by oldfred on 2013-04-09
My typical suggestion, but if you want to experiment with other installs you might need additional partitions or more space for data, so you can vary depending on your needs. If not sure you do not even have to allocate entire drive originally. I did that with my new drive a couple of years ago, but now it is almost full of 25GB test installs that should be housecleaned.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

