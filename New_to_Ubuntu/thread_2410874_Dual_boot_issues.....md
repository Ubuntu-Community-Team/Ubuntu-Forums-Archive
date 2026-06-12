---
title: "Dual boot issues...."
date: 2019-01-21
forum: New to Ubuntu
---

### Post by jfbertrand on 2019-01-21
My dual boot lenovo will not boot and is showing ..  Checking media...nthen efi network 0... Boot fail
So i tried the boot-repair but it did noting for me... No changes
I dont have a current backup so im hopping to not do further damage...
[Http://paste.ubuntu.com/p/RvMBSTdnxQ/](Http://paste.ubuntu.com/p/RvMBSTdnxQ/)

If i could get a few hits that would be greatly appreciate d ...

---

### Post by oldfred on 2019-01-21
You have a new UEFI system. Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives for last 5 years.
But you installed Ubuntu in the now 35 year old BIOS/MBR configuration.
How you boot install media, UEFI or BIOS is how it installs. 
But then you UEFI must be set to boot in that mode. You may have UEFI trying to boot in UEFI mode with BIOS install.

Might be better long term to reinstall in UEFI boot mode.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by jfbertrand on 2019-01-22
So can i just re-install  with uefi over my old ubuntu bios ? Will i lose my data ?
Thanks

---

### Post by yancek on 2019-01-22
> So can i just re-install  with uefi over my old ubuntu bios ? Will i lose my data ?

You can re-install Ubuntu to the same partition(s) you originally installed it.  If you haven't been able to boot Ubuntu, what data are you referring to?  It may be possible to convert Ubuntu to UEFI mode which is explained at the official Ubuntu documentation site below.  It also explains the proper way to install UEFI in a dual-boot scenario.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-01-22
And reinstall in different boot mode will convert drive from MBR to gpt in effect erasing it.
Make sure you have good backups.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by jfbertrand on 2019-01-22
ive been using my dual boot setup for more than a year now and have lots of pics and documents on the ubuntu partition... i would like to copy that data to a usb drive but i cant figure out yet how to do so via Try ubuntu.
Bio will show hhd and i can see the partition via the disk utility on Try ubuntu ... but Try ubuntu will not show it as a drive i can copy from ... been looking into terminal command lines to mount the hhd but this is a bit over my pay grade lol
once i get a safe backup i will re-install with UEFI but last i recall my lenove c710 was not allowing it ... one dog at a time ;-)
thanks for you support !

i think the mounting issues are from not being admin to mount the main  partition ... ? made a picture of the drive im looking to boot into or  copy ...

[IMG]http://www.jfbertrand.ca/uploads/2019-01-23%2000-36-22.png[/IMG]

jf

---

### Post by oldfred on 2019-01-22
You may have to manually mount. And probably ro or read only.
Live installer uses user 999 as default and an install is user 1000 for the first user, 1001 for second, etc.

If you chroot into system, then you are only using live installer as kernel & drivers, but rest of system is your install.
       To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by jfbertrand on 2019-01-26
Hi ....
Just wanted to share how i managed to get my system back...
Making a bootable uduntu was a major helper in mode 'try ubuntu' and allowed me to learn by trial and errors.
Testdisk was a big helper in allowing me to see my lost files and copy then before attempting a full ubuntu install. The copy utility is very basic and gives no status so it makes it hard to figure out. It works so keep that in mind... Make sure try ubuntu can see your external usb drive... That is not full &#128512;... The copy ask for copy location but even if you select a dir on your drive it will copy the hole dir tree in root.... Can get confusing when wanting to confirm copy... Make sure you hide deleted files before copy as this will crash it otherwise... Copy one dir at a time not the full tree... 
So i made my backup of essential files ... 
Then installed ubuntu over the hole disk.... It actually detected my old partition and offered to keep it as a boot option ... Keeping my files on drive ..  Nice ! 
It worked except i cant boot on the old partition ... Giving size error but i can copy my files easy in the new installation to my external drive... 250g &#129299;
I then re- install ubuntu with a clean full disk format... I think im getting good at this lol
Anyway ... Just keep at it and you will prevale
May the forces be with you linux tribe
Ps: sorry about the spelling.... Im french &#129299;

---

