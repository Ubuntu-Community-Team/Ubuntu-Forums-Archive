---
title: "Dual boot windows 8.1 with ubuntu already installed"
date: 2015-03-06
forum: New to Ubuntu
---

### Post by vishal_ on 2015-03-06
How do i install windows 8.1 alongside a pre installed ubuntu 14.04. I have few softwares and games which run only on windows and i have received the official copy of windows 8.1 by my university. I have ubuntu installed already in my laptop as the only os. How should i proceed as i find very less help in the internet on this topic. Consider me as a rookie in ubuntu as well.

---

### Post by oldfred on 2015-03-06
How is Ubuntu installed UEFI or BIOS. 
And what partitioning have you used gpt or MBR(msdos).
Post this:
sudo parted -l

Windows only installs to gpt partitioned drive with UEFI and only to MBR with BIOS boot. 
With MBR it must be installed to a primary NTFS formatted partition with the boot flag.

If newer hardware that is UEFI with CSM or BIOS boot modes, how you boot installer is how it installs. If partitioning not correct it will just erase drive to convert to type of partitions it wants.
And with MBR it does not correctly see Linux partitions, so backup MBR partition table with sfdisk.

---

### Post by vishal_ on 2015-03-08
now there is a serious issue :( 
ubuntu doesnt load at all... the dotted screen keeps continuing forever
i used a liveusb and tried use try ubuntu without installation... its the same loading screen which loads forever.. i tried boot-repair-disk.iso in a live usb... not much success in it as well... there are no data available... the laptop is brand new pre installed with ubuntu... the problem occured when i updated ubuntu to 14.04 and it stopped unfortunately in the middle without completing the update... i have a live usb of windows 8.1 as well... and i have a live usb of ubuntu as well.. i really need some OS working ... i would be happy to dual boot win 8.1 with ubuntu... i dont care whatever data is there since its brand new.

---

### Post by oldfred on 2015-03-09
What brand/model computer?
What video card/chip.
You many need boot parameters at grub screen particularly nomodeset for video or settings if Intel video.
And/or you  may need to change various UEFI/BIOS settings.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

