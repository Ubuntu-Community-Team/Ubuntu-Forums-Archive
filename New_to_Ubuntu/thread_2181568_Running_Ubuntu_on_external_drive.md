---
title: "Running Ubuntu on external drive"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by Kevin_newbie on 2013-10-18
Hi everyone, 

I am trying to run Ubuntu 12.04 LTS side by side with Windows 8.  I attempted to shrink my internal C drive, after defragging, and it told me I only could shrink it by 4 GB, despite having 100 GB free. I gave up on this route and decided to try and install on an external drive via a USB 2.0 connection.  Not ideal, but should get me going. 
It seemed to work OK. However when I tried rebooting, I couldn't boot and got the Grub Rescue shell, unless I had the External drive connected, when I could boot into either UBUNTU or Windows. This is despite the fact that I changed the BIOS order to direct booting to occur from the internal hard drive. 

Tried to fix it using this

 [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

To be honest, it was a case of 'monkey see, monkey do'. I had no idea what I was doing. The explanation looked plausible, but the commands were a mystery. Now it always boots to Windows 8, whether the external drive is connected or not. Any ideas how to fix this, without removing access to Windows 8?

Thanks to all the good people who respond. I really appreciate it. 

Have a nice weekend.
 Kevin 

>

---

### Post by andreazzz on 2013-10-18
Well, I think the problem is that you have installed GRUB on your internal HDD with references to a external drive and probably GRUB has problems with that. The only way you can fix that is attaching your external HDD to your pc, booting into Windows and shrink your Windows partition so that you can install Ubuntu on that. Restart on your Ubuntu-installation-medium and install it on your SDA (first hard disk, internal). You should mind installing GRUB on SDA (2), so you can detach your external HDD.

---

### Post by fantab on 2013-10-18
Looks like you installed Grub to the Internal HDD, but all your Grub Files are on Ext. HDD, that is why you need Ext HDD to successfully run Grub.

Is this a laptop with pre-installed Windows 8? Share some details about your machine.

What you can try is to reinstall Grub to your External USB HDD and then fix Windows Boot. Does Windows 8 boot with UEFI or Legacy BIOS.

Boot Ubuntu from Ext. HDD and run following commands in the Terminal:

```
sudo dpkg-reconfigure grub-pc
```

After running this command you will be presented with options, go through them carefully and install Grub to your Ext. HDD.

Then fix the Windows 8 Boot, here we need to know if Win is boot with UEFI or not.

Alternatively you can use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") utility to reinstall Grub to your Ext. HDD.

---

### Post by Kevin_newbie on 2013-10-18
Hi there,
It is an old PC, with BIOS, no UEFI issues. I installed Windows 8. I am not in a position to run Ubuntu at all at present, Windows launches regardless of whether the external drive is plugged in or not.
I guess the boot repair disk option sounds good. Windows boots fine so I don't think I need to repair it, or do I? I need to make sure to repair the correct disk, I do not want to damage my Windows install....
AFAIK I had installed UBUNTU to a 25 GB partition on the external HDD. 
Thanks again for your input, will let you know how I get on., 
Kevin

---

### Post by Bashing-om on 2013-10-18
Kevin_newbie; Hi !

Here is a thought, you may install grub onto that 2nd hard drive, and not even touch Windows' boot code on the 1st hard drive. But that does entail selecting in bios what hard drive to boot from. Windows is booting fine, leave well enough alone as selecting to boot the 1st hard drive in bios should always give you the ability to boot up Windows.

You may install grub to "sdb" using a liveDVD/USB, and once installed and working, chainload Windows' boot code into grub. With the 2nd (sdb) drive set as the  1st boot priority in bios, you may then have the choice of what operating system to boot.

[INDENT]one solution of many
[/INDENT]

---

### Post by mc4man on 2013-10-18
I'm running Ubuntu now from an external ssd drive,  the best approach I found was when installing Ubuntu is to install the bootloader to the external drive
(by default the installer will use your internal drive so you must change that on the partitioning screen during install.

Then it's simply a matter of choosing which drive to boot to, external for Ubuntu or internal for windows

---

### Post by fantab on 2013-10-18
In BIOS you have to choose to 'Boot USB devices first' or something of the sort. So when Ext. HDD is plugged in it will boot, when it is not then INT. HDD will boot.
If Windows is booting fine on its own then you don't have to FIX its boot.
You just need to reinstall Grub or perhaps Ubuntu itself again to the Ext. HDD. But make absolutely sure that you install Grub to your Ext. HDD.

---

### Post by Kevin_newbie on 2013-10-21
Hi everyone,
  I am posting this response from Firefox running in Ubuntu.! I ran Boot Repair with the recommended options and all is well. Thanks to all the good people who took time out to respond to my call for help. Very kind of you all. 
warmest regards
 Kevin

---

