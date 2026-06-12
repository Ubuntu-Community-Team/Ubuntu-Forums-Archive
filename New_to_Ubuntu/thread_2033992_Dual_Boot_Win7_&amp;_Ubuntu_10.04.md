---
title: "Dual Boot Win7 &amp; Ubuntu 10.04"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by DarthBrute on 2012-07-27
Alright weird situation. Even though I have internet access I do not have internet access to the laptop I am trying to fix. (Currently on deployment and I can't connect my personal laptop to the internet.) I can download tools and transfer them to my laptop though.

Anyway.....

Sometime ago I had Vista. I downloaded 10.04 and installed it. Boom dual boot. Sometime later I upgraded to Win7. Dual boot goes bye bye. Well it has been well over a year since I have done anything with ubuntu. But I needed a project and trying to bring back my Ubuntu sounded like a good one.

I have a live CD of 10.04, I can not connect my personal laptop to our network onboard the ship for internet access.

I need a way to bring back my partition. It is telling me to enable the component called 'universe' I figured out that is the ubuntu community (correct?) 

I need some good commands to run on this baby.

Also..Could I install on top of the partition (just by selecting defaults) without destroying already downloaded programs, pictures, files, etc?

Thanks for any help you could give me.

---

### Post by techvish81 on 2012-07-27
the grub has been overwritten by windows , you need to reinstall grub or  you can boot ubuntu cd, install grub rescue and run it.

actually you should think about an upgrade, 10.04 has reached end of life and you will not get security updates on it, soi in my opinion you should :

1) backup your important data by running live cd.
2)while in the live session, run gparted and format the ubuntu partition.(carefully, not the windows partition)
3)install the latest 12.04 LTS with 5 yrs of support by selecting the option "install alongside windows" in the installer to keep your dual boot.

---

### Post by DarthBrute on 2012-07-27
Already looked at those options. But I can't connect to the internet to get them.

---

### Post by oldfred on 2012-07-27
If you have a bootable liveCD, you can reinstall grub2's boot loader. Most of our instructions now assume Internet access, but since liveCD is same version, this should work.

Do you have Windows repairCD? If not make that first.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

If you do not have Windows repair, you should back up MBR, just in case the install of grub does not work. You need some way to get back and Computers only boot thru MBR on hard drive. So you need working repairCD or liveCDs to fix things.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

Basically:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

dd is also know as Data Destroyer. Only run this if you have no other way to restore the Windows boot loader and triple check that you typed it correctly. Any error with dd usually destroys system, but it can be a powerful command to do things.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

---

