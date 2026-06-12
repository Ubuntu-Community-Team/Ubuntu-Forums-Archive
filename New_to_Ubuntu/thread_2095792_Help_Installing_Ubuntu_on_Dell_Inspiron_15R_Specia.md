---
title: "Help Installing Ubuntu on Dell Inspiron 15R Special Edition"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by AlwaysDroid on 2012-12-18
Hi all,

I have a Dell Inspiron 15r Special Edition. It has Core i-7 (64bit), 8gb ram , 32GB SSD  and TB HHD.. I bought it from dell and have not done any mods.

I am having a hard time installing ubuntu on it (64bit 12.10 desktop). (Md5 OK).  It boots up from the disk image I burned (chose "install ubuntu" from grub), past connecting to wifi and then comes up with this: 
```
https://www.dropbox.com/sh/zyjf6zo68zx5njp/ZF_iwqA--V
```All pictures are there ^^^^^^

I tried the 32 bit version on my  desktop computer (Single HHD, Pentium 4, 1gb ram, 32 bit :P) and it came up asking if i wanted to install along side or  replace windows. I never got that on my laptop. I think it is a problem  with the set up off the SSD, can anyone help me?

Ps: The layout of the SSD is just plain wierd, I added a picture of it to the dropbox. There is a 35 Gb SSd, that is showing up as a partition on the primary TB drive. I dont get it :/

---

### Post by oldfred on 2012-12-18
Welcome to the forums.

Is this Intel SRT? That uses RAID which the Desktop installer does not have drivers for. Most turn off the SRT and then install. Some have totally disabled SRT and installed Ubuntu's / (root) to SSD with /home on rotating drive. Others install Ubuntu to rotating drive and then turn SRT back on.

Also is this a new Windows 8 pre-installed system? If so you also have secure boot.
[http://askubuntu.com/questions/187144/is-dell-inspiron-15r-special-edition-compatible-with-ubuntu](http://askubuntu.com/questions/187144/is-dell-inspiron-15r-special-edition-compatible-with-ubuntu)

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel RST issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
Different model but Dell. 

 Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by centaurusa on 2012-12-18
> **AlwaysDroid said:**
>  
Ps: The layout of the SSD is just plain wierd, I added a picture of it to the dropbox. There is a 35 Gb SSd, that is showing up as a partition on the primary TB drive. I dont get it :/

I suspect what you have is a 35 GB SSD being used as cache for the 1 TB hard drive.  Intel software tells the operating system to use both disks as a "single" drive.  Frequently-used files are stored on the SSD so that accessing these is very fast.

See:  [http://en.wikipedia.org/wiki/Smart_Response_Technology](http://en.wikipedia.org/wiki/Smart_Response_Technology)

---

### Post by AlwaysDroid on 2012-12-18
Thanks for the responses guys. And I'm not sure about the raid set-up, i will check though. It is windows 7 home premium, and secure boot is off. 

As for the cache, i will check into that also and reply back if find anything, or cant get it to work. 

Thanks again!

EDIT: Yes, it uses intel rapid store technology. I will disable it and then install ubuntu to the rotating disk. Will probably make things alot easier than putting ubuntu on the SSD and then using the rotating for /home. Unless it is, and then tell me!

Also, if i turn off the intel rapid storage, can i turn it back on after installing ubuntu? Basically I would like windows to be set up exactly as it is now (rapid storage on) and have ubuntu along side somewhere.



Edit 2: It was late last night when i wrote this and i was tired, i actually have a 32 gb sata SSD not 35gb haha. My bad, not like it matters though.

---

### Post by oldfred on 2012-12-18
Do not know details on Intel SRT, but a couple of users posted in the threads I linked to on turning it back on.

---

### Post by AlwaysDroid on 2012-12-18
> **oldfred said:**
> Do not know details on Intel SRT, but a couple of users posted in the threads I linked to on turning it back on. Thanks, will go and read them all :)

---

### Post by AlwaysDroid on 2012-12-19
Hey, i used the method here: scroll down to asymptoticFault's long post. (also used his other one a bit down from long one)


[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

I successfully installed it using sudo dmraid -E -r to find the disks. 
i rebooted, re-enabled SRT and rebooted. 

no grub, windows ran chkdsk and booted. SRT works. No ubuntu though :(

Edit: going to use boot repair. I installed from terminal, just posted in the thread.

---

### Post by oldfred on 2012-12-19
I believe everyone that got it to work disable Intel in Windows and removed the RAID settings meta-data on the drive. Then Ubuntu installed and worked.

Some installed directly to SSD as Windows was actually only using part of it and they did not want Windows that much. Others installed to hard drive and were able to turn the Intel back on. 

But I do not think you can turn the RAID back on until you have Ubuntu working. And once you turn it on again, you would have to remove RAID settings again. 
You may be able to add the RAID drivers so Ubuntu works once RAID is set up again.
       sudo apt-get install mdadm

---

### Post by AlwaysDroid on 2012-12-20
> **oldfred said:**
> I believe everyone that got it to work disable Intel in Windows and removed the RAID settings meta-data on the drive. Then Ubuntu installed and worked.

Some installed directly to SSD as Windows was actually only using part of it and they did not want Windows that much. Others installed to hard drive and were able to turn the Intel back on. 

But I do not think you can turn the RAID back on until you have Ubuntu working. And once you turn it on again, you would have to remove RAID settings again. 
You may be able to add the RAID drivers so Ubuntu works once RAID is set up again.
       sudo apt-get install mdadmThanks a ton! I tried that, but i get unknown command.

---

### Post by arbex5 on 2013-04-05
I was having the same issue.
To FIX you just need to create a partition on the rotating disk with 100mb and set it as bios_grub in file system with the help of gparted.

Here is how my partition is 

/dev/sda (rotating disk 1TB)

Partition      filesystem    Mount Point    Size          Used       Unused       Flags
/dev/sda1    unknown                         100.00MiB                                 bios_grub
/dev/sda2    ext4            /home          931.32GiB  15.11GiB  916.20GiB    
/dev/sda3    ext2            /boot            100.00MiB  38.60MiB  61.40MiB 

/dev/sdb (flash disk 32GB)

Partition      filesystem    Mount Point    Size          Used       Unused       Flags
/dev/sdb1    ext4            /                  25.14GiB    3.14GiB   22.01GiB    
/dev/sdb1    swap

Hope it helps

---

