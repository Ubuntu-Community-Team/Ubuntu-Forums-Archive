---
title: "Using grml-rescueboot to boot using an ISO on another partition"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by ogp on 2014-04-27
Hello, 

I am trying to use grml-rescueboot to install an updated version of Ubuntu on a machine I have. My understanding of what is going on (and what is therefore going wrong) is hazy but I am sure the problem I am encountering is simple, and yet I can't understand how to solve it. 

There is only one HDD, in four partitions. 1 - Win XP, 2 - Existing Ubuntu 13.04 installation, 3 - Ubuntu swap file, 4 - Storage area, which mounts at /media/Icarus. 

I have installed grml-rescueboot on the machine, and have an ISO of 14.04 in /boot/grml on the system partition of the existing installation (i.e. in partition 2). I want to use grml-rescuedisk to install Ubuntu 14.04 on partition 2 of the disk, overwriting the existing installation. 

I can boot to the ISO very easily by choosing it from the GRUB menu, but if I try and install 14.04 on partition 2 then it never gets past the "checking filesystems" part of the installation - I presume because I am asking it to install over the top of the ISO which it is reading from. (Is this a correct assumption?) I have tried adding the line ' [COLOR=#000000]CUSTOM_BOOTOPTIONS="toram" ' to the file [/COLOR][COLOR=#000000]/etc/default/grml-rescueboot, but this causes the installation to fail differently; it asks me whether I want to unmount /isomount, and freezes at that point. 
[/COLOR][COLOR=#000000]
One solution for this would be to ask grml to use an ISO which is mounted in partition 4, which I currently use for storing documents and which is not to be written over. This would overcome the problem as I understand it. 

The question therefore is how do I set grml to do this? If I select the grml option in GRUB and press "e" then I can see the detail of the grml entry but I can't understand how to edit this to achieve what I want. As I said, my understanding is quite basic so please do post me to a simple web page explanation if this is an easier way forward. 

Thanks, 


Oli. 
[/COLOR]

---

### Post by oldfred on 2014-04-28
I have not used grml-rescueboot, but have done it manually.

But booting into the install you are overwriting seems like it will lead to issues. I have all my ISO in another drive and use grub2's loopmount to mount it.

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

My iso folder in in drive 2 partition 4 and is gpt partitioned (part_gpt). Yours would be drive 0, and partition 4?
And you probably have msdos(MBR) partitioning and probably do not even have to tell that to grub. 
I also have nVidia and add the nomodeset to the linux line.

```
menuentry "Ubuntu 14.04 Trusty ISO 64bit" {
    set isofile="/iso/ubuntu-14.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by ogp on 2014-04-28
Oldfred, 

Thanks for your answer - that's helpful. 

What does the loopmount bit do? As in, your code with my comments would look like this (with the bits which are bothering me in **bold**); 

 ```
[COLOR=#000000][FONT=Ubuntu Mono]menuentry "Ubuntu 14.04 Trusty ISO 64bit" {[/FONT][/COLOR]    [COLOR=#ff0000]#This is the heading which appears in the GRUB2 list[/COLOR]
    set isofile="/iso/ubuntu-14.04-desktop-amd64.iso" **[COLOR=#ff0000]#This is clearly the path to the ISO which is being booted from, but *where is it mounted?* [/COLOR]**
    insmod part_gpt [COLOR=#ff0000]#This tells the system about the formatting of the partition that your ISO is being read from[/COLOR]
    loopback loop (hd2,4)$isofile [B][COLOR=#ff0000]#This is probably the answer to my "*where is it mounted?*" question above - the complete path could be written "(hd2,4)/iso/ubuntu-14.04-desktop-amd64.iso". However, if 
  this is the case, then why is it split up over several lines? Have I missed something? [/COLOR][/B]
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset    initrd (loop)/casper/initrd.lz [COLOR=#ff0000]#This is a collection of settings (nomodeset, 
  as you are using nVidia chips) and some other bits which I don't quite understand. [/COLOR]
}
```

Putting it another way, does the loopmount bit simply give the path in the first line the root upon which it is mounted? 

As it is (and I will try your suggestion - thanks again), I suspect that I have other problems here. I have tried creating another partition on the hard drive and installing to this partition using the iso that is within the previous partition and this failed in the same way (it gets to "Checking file systems" and hangs there.) I don't understand what is going on and need to spend some more time working on it. 

Thanks for your help none the less. If you can help me understand loopback a bit more that would be appreciated, but don't sweat it if you don't have time. 


Oli.

---

### Post by oldfred on 2014-04-28
The set iso is the path and file name together.

My partition has many folders all at top level. Normally I mount it which adds to the path, but when grub is booting the mount does not yet exist to it is just the folder /iso in my sdb4 partition.

I use the set isofile command as the exact file name has to be in two places, loopback line and linux line. And I found it easy to change one, but not the other and create all sorts of issues.

When booting with grub drives are not sda, sdb, but hd0, hd1. But the boot drive is always hd0. And the rest of the  drives may vary. Mine are normally in the sda, sdb order which matches the port order on my motherboard. But I must have skipped a port, so a flash drive is sde when mounted, but sdb when rebooted which changes my numbers all around. Or I had to experiment which works using the e for edit on grub menu.

So my drive with the the 4th partition having a folder called /iso is hd2 when I normally reboot. If you only have one drive it is simple and just hd0. 

I do not always understand all the other little bits either. Each distribution that can boot from a ISO directly (not all can) have different boot parameters. I often have to mount ISO and look at the syslinux or boot configuration files to find the standard boot parameters used. Thats why the examples link is good as those usually are correct. But even Ubuntu changed and added a .efi to vmlinuz even if not an UEFI install with recent versions.

---

### Post by ogp on 2014-04-28
Thanks. I think I followed most of that - thanks for the explanation. 

Putting a more practical spin on it, I have now tried to install it again, using the following entry in GRUB2; 

```
menuentry "Ubuntu 14.04 ISO" {
        set isofile="/iso/ubuntu-14.04-desktop-i386.iso"
        loopback loop (hd0,4)$isofile
        linux (loop)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile 
        initrd (loop)/casper/initrd.lz
}

```

GParted tells me that the partition that the ISO file is on is sda4 (hence (hd0,4)) and it's in /iso in that partition. 

It ran from the ISO fine, and when I tried to install it to sda2 (partition 2 on the only hard drive) then it produced the following messages; 

"The installer has detected that the following disks have mounted partitions: 
/dev/sda
Do you want to try and unmount these before installing?"

I don;t understand this as I'm not sure why there is anything mounted; I am booting from an ISO file in partition /dev/sda2. However I answered "No" (I don't want to unmount things), point the installer at sda2, tell it to format it as ext4 and to use this partition as '/' as the mount point. 

The following message then appeared: 

"The installer needs to commit changes to partition tables , but cannot do so because partitions on the following mount points could not be unmounted: 
/isodevice
Please close any applications using these mount points. Would you like the installer to try to unmount these partitions again?" 

If I click "OK", it runs through to "Detecting file systems" and hangs again ... back to square 1. 

Given these things, is my problem something to do with the way I am mounting partitions or something else? 

(An aside, but I have ordered a USB memory stick which should arrive tomorrow. I am hoping that this will be the 'silver bullet' to solve this as I can then install using unetbootin and the USB stick, but I'd quite like to know what I am doing wrong with this method as well.) 

Thanks again for your help. It really is appreciated. 


Oli.

Extra Detail (probably irrelevant): the machine is a laptop, plugged into a network cable, and I asked the installation to download updates and the additional software.

---

### Post by oldfred on 2014-04-28
I am doing it from another hard drive or from a flash drive, so I do not know about same drive issues.
And I get the unmount question and say no.
As long as you are using a primary partition and not resizing a partition,it I would think it should work. 
But since you are formatting it, it must have to write to partition table, and must want to rewrite the entire partition table not just the one partition. 
Try unmounting, as then it may run from RAM if you have enough.

---

### Post by ogp on 2014-04-29
Oldfred, 

Thanks again. Your input is really appreciated. Having done a bit of poking around, it seems that the problem is caused by the fact that there is an ISO on Partition 4 which is mounted which prevents the installer from either formatting or wiping the partition that it is being pointed at (i.e. partition 2). I understand that these are both partitions on the same drive, but I can't understand why having one mounted would prevent installation from taking place on the other. Any ideas? 

I tried your suggestion of unmounting and that didn't make any difference. As I write this I realise that I could unmount it manually from the terminal - maybe I'll try that. 

Thanks again, very much, for your help. 


Oli.

---

### Post by oldfred on 2014-04-29
Before I started using another hard drive, I used flash drives. 
But rather than the standard install, I just installed grub to flash drive, created my own grub.cfg manually and booted one of several ISO on flash drive. It originally was 4GB flash and I did not want to 'waste' the space of a single installer. I was able to put several ISOs on one flash drive, so I had Ubuntu, gparted, parted magic  and one or two other small ones. I did this primarily as before I would burn CDs for the current version of each of the repair ISOs so I had many ways to boot.

       Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot


 Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by ogp on 2014-05-07
OldFred, 

Thanks again for your help with this one. As it is, I failed to make it work in any way using an *.iso on the root of any drive - it always halted at the "Detecting File Systems" stage and didn't get any further. I still suspect it is due to the fact that there was an *.iso mounted, but am also aware that this is not a full explanation. 

In the end I bought a memory stick (hey, I needed one anyway!) and used that, and it worked a treat! (On that basis I'm not sure whether to mark this thread 'Solved' or not. I think not, as I didn't solve the original problem.)

Thank you for your help none the less - it was genuinely appreciated. 


Oli.

---

### Post by oldfred on 2014-05-07
I have 4 drives and many installs so the detecting file systems takes a while.
But if you have corruption on any partition it fails in scan of system. 
Does gparted show all partitions without a warning or error icon? If you have icon click (or maybe right click) on it and see what it says.

Several years ago when still using XP, I had to run chkdsk on the NTFS partition. XP booted but after chkdsk it booted a bit faster also. But until I ran chkdsk nothing Linux would see the NTFS partition even though with XP it worked.

---

