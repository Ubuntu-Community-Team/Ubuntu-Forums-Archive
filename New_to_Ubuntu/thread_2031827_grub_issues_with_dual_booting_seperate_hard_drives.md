---
title: "grub issues with dual booting seperate hard drives"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by G4dget on 2012-07-22
Ok, So I searched around on here and found multiple threads to help with dual booting issues but none of them seemed to work for me. I have dual booted before but after a re-install of windows xp x64 (which erased my ubuntu drive) and a subsequent re-install of ubuntu 10.04.4 I am unable to get grub to see that I even have windows installed on another hard drive. I am going to attach the results of bootinfoscript and give a quick run down of drives.

sda - ntfs partition only ever used for storage. I think ubuntu install put grub here

sdb - ntfs windows xp x64 is only thing on this drive ( windows install put ntldr on sdc mbr which erased sdc since it had pre-existing ubuntu install)

sdc - ext4 ubuntu 10.04.4 amd64 fresh install put grub on sda i think. (this is what I used to boot from before all this mess happened. I have grub now on this drive and am able to boot ubuntu using either grub on sda or sdc

End result would be to get rid of grub on sda and make sdc grub boot ubuntu and windows. 

```
sudo update-grub
```

returns with just ubuntu and memtest being added to boot

```
sudo grub-install -v
```

returns with - grub-install (GNU GRUB 1.98-1ubuntu13)

I'm not sure if I just need to modify a script for grub.cfg or what since so many of the grub issues posted on here have different setups I could not find one that seemed to fit my issue.

---

### Post by NikTh on 2012-07-22
Hi , 
boot to ubuntu and try to mount the drive that has windows boot files. 
When you mount it , open a terminal and run
```
sudo update-grub
``` 

Thanks

---

### Post by G4dget on 2012-07-22
It mounts fine and I can see all the files. 

Running 
```
sudo update-grub
```

returns
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-23-generic
Found initrd image: /boot/initrd.img-3.0.0-23-generic
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by NikTh on 2012-07-22
Hi , 
did you try to run [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ?

Thanks

---

### Post by oldfred on 2012-07-22
You are not showing in bootinfo script any Windows boot files in the NTFS partitions???

Script should have found these.
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

And Windows puts a boot flag (active partition) on the NTFS primary partition it expects to boot from. Only sda1 has a boot flag, and you do not have boot flags anywhere  on sdb or sdc. Grub does not use boot flag, so usually it is ok, but a few BIOS expect a boot flag and will not start boot process unless it sees a flag. So I normally suggest a boot flag on a primary partition on every drive.

---

### Post by G4dget on 2012-07-22
@oldfred

I just noticed this as well while I was looking at another thread about boot issues. I have since gotten ntldr and ntdetect added to mbr on sdb and now grub recognizes windows xp. not sure if it boots yet as I have two separate grubs now. One on sda and one on sdc. I'm going to tell my bios to boot from sda to test windows boot ability but I want to get rid of this grub and only use grub that is on sdc.

@nikth

Is boot-repair able to remove installs of grub or just repair them?

---

### Post by oldfred on 2012-07-22
You do not need to remove grub2 from a MBR or PBR. You just overwrite it when needed with whatever boot loader you want. I like to keep the boot loader on the same drive as the system install when you have multiple drives. Or Windows drive has Windows boot loader and Linux drive has Linux boot loader. 

Set BIOS to boot from sdc and use sdc to boot. If you installed to sda initially, grub remembers that to reinstall on major updates. 

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by NikTh on 2012-07-22
> **G4dget said:**
> @oldfred

I just noticed this as well while I was looking at another thread about boot issues. I have since gotten ntldr and ntdetect added to mbr on sdb and now grub recognizes windows xp. not sure if it boots yet as I have two separate grubs now. One on sda and one on sdc. I'm going to tell my bios to boot from sda to test windows boot ability but I want to get rid of this grub and only use grub that is on sdc.

@nikth

Is boot-repair able to remove installs of grub or just repair them?

Hi , 
if you problem is missing window's (boot) files , then no , boot-repair can't fix this problem. 
Boot-repair just search and install grub , when its possible and when grub missing or false installed.

Follow @oldfred's suggestions. He is more experience with these issues. 

THanks

---

### Post by G4dget on 2012-07-23
I'm going to mark this as solved. 

With the help of @oldfred I noticed that I was missing boot.ini/ntldr/ntdetect.com on my windows drive sdb(I believe these were installed on sdc where I installed linux after windows which resulted in there deletion.)

Using my windows xp cd I booted into the recovery console by letting the cd load install and then selecting repair at the first option screen. This takes you to a command line with Recovery Console specific commands.

I copied new ntldr and ntdetect.com from the [cd.drive.letter]:\i386\ to the root of sdb. This allowed grub to recognize the installation using

```
sudo update-grub
```

Now when I booted and selected windows from grub screen it gave me a no boot.ini file found but went ahead and booted to windows just fine anyway but to just make everything nice and clean I went back to recovery console and used 

```
bootcfg \rebuild
```

This will scan all drives to look for windows installs and ask you which ones to add to the boot list. ( Didn't work for me though I used slightly different load identifier and ended up manually editing the boot.ini inside of windows by right clicking My Computer, properties, then going to the advanced tab and selecting settings of startup and recovery then selecting edit)

This is a copy of what is in a different windows laptop i have. I believe this should be sufficient to any windows xp install as this is also what my desktop reads. Do your research on this one just in case and assuming bootcfg doesn't work for you either

> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


Once you select the one you want to add here are the questions and I believe the correct responses to them 

OS Load Options = /Fastdetect
Load Identifier = Microsoft Windows XP Professional

If this works then all that is left is to set the attributes for the three files from Recovery Console. Using the Attrib command to make them read-only, system files and hidden. You need to run these for each file to set the attributes.

```
attrib +r c:\filename
attrib +h c:\filename
attrib +s c:\filename
```

Now when I select windows from grub everything goes normally and windows startup screen comes on and windows loads as it should.

This was more a windows problem then grub or linux but with so many people dual booting it should be helpful to have all of this in one place.

---

