---
title: "duel boot win7 with ubuntu 12. bootloader install fail. /dev/sda"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by itslindseytime on 2014-01-25
ok so i have looked through the forums and no other question is exactly like mine. i have a fresh install of windows 7. i partitioned the disk through windows (left about 200 gigs saved for ubuntu) and then went for a fresh install of the most recent steady ubuntu. it installs fine until i get message at the end:
executing 'grub-install /dev/sda' failed. this is a fatal error.

the only other options of places to install it is:
/dev/mapper/isw_cajaiejdcd_M14XR2_RAID0

they all start like that. the endings are: 
RAID0 linux device mapper (striped) (512.1 GB)
RAID0p1
RAID0p2 windows 7 (loader)
RAID0p3
RAID0p5
RAID0p1 linux device mapper (linear) (41.1MB)
RAID0p1
RAID0p2 Linux device mapper (linear) (11.5 GB)
RAID0p2 windows 7 (loader)
RAID0p3 linux device mapper (linear) (290.9 GB)
RAID0p3
RAID0p4 linux device mapper (linear) (209.7 GB)

so there isnt a /dev/sda option even listed. and i dont know what to do. my computer is an alienware laptop less than 2 years old, best one they made at the time, so i dont think its a computer issue. i am a complete noob. please make sure the answer is appropriate for a noob. please help!!!

---

### Post by fantab on 2014-01-26
Its a RAID thing. I am not exactly sure how to go about Installing Ubuntu on a RAID system, but IIRC you must disable RAID first.

Take a look here: [http://askubuntu.com/questions/43036/how-do-i-install-grub-on-a-raid-system-installation](http://askubuntu.com/questions/43036/how-do-i-install-grub-on-a-raid-system-installation)
More Info on RAID:
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by oldfred on 2014-01-26
I would not disable RAID.
But standard desktop installer does not support RAID (yet). With 12.04 there was an alternative installer that included the RAID & LVM drivers for desktop installs. Plan was to add those features to gui install, but so far only LVM has been added. 
It seems installer does now see RAID and install but grub does not yet see it?

You install grub to root of RAID not MBR of drive. The root of your RAID looks like RAID0 without any pX or partition info at end of RAID.

Boot-Repair will add the RAID driver and let you choose to install RAID. But use manual and install to RAID0 not sda.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info]("sehttps://help.ubuntu.com/community/Boot-Info")
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

    
I do not really know RAID, as there are many types. Yours may be the BIOS type which is also called fakeRAID as is just BIOS software not hardware.
 This is for a nVidia type RAID.
 For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

It looks like your install is in p2, so if manually installing grub you mount /dev/mapper/isw_cajaiejdcd_M14XR2_RAID0p2 and install to/dev/mapper/isw_cajaiejdcd_M14XR2_RAID0.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

---

### Post by itslindseytime on 2014-01-27
You install grub to root of RAID not MBR of drive. The root of your RAID  looks like RAID0 without any pX or partition info at end of RAID.

Boot-Repair will add the RAID driver and let you choose to install RAID. But use manual and install to RAID0 n

my computer actually had an ubuntu option when i was building it online. it asked if i wanted that or win 7. i figured when i got it i could just duel boot since ubuntu is free. now im kicking myself. lol. so the question is what exactly should i do? wait for a newer ubuntu to come out that supports raid? or should i try to install it a different way? sorry for being such a noob with this im sure its annoying. if i install it the way you said and install it to RAID0 will it install over my win7? and thanks so much for the reply :)

---

### Post by itslindseytime on 2014-01-27
i have an intel rapid storage technology solid state drive. if that helps any.

---

