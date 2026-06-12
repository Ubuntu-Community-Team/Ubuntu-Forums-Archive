---
title: "install kubuntu on external hardrive, size allocation"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by mmsmc on 2013-05-07
Hi

I have a 1.5 TB external hard drive I am attempting to install kubuntu on. It is not bootable in BIOS so I was told to format it from ntsf to exfat. I am wondering, what allocation size unit should I use? it ranges form 128 kilobytes to 32768 kilobytes

Thanks
mmsmc

---

### Post by fantab on 2013-05-07
First of all you don't have to format the whole drive to FAT. You just need to create 30GB partition ext4 and to install Kubuntu, a small 2-4GB SWAP partition. That should do.
You should also enable in BIOS USB boot (if your external HDD uses USB).

Can you tell us more about your machine? things like, does it have UEFI? are you dualbooting with windows7/8?

---

### Post by mmsmc on 2013-05-07
I am currently running windows 7, no dual boot, and no i do not have UEFI. The external hardrive I am trying to install onto is not being recognized in kubuntu(I currently have it on a usb drive) and am unsure why. I am also unable to find any clear instructions on how to approach this

Thank you for our quick reply

---

### Post by fantab on 2013-05-07
Check you BIOS settings and see if it allow to boot an USB. You may have to 'enable' usb boot. What happens when you boot Kubuntu USB? Does Windows recognize your USB?

---

### Post by mmsmc on 2013-05-07
yes windows does recognize it as a usb, so does my BIOS. I can boot from it, but nothing loads, as nothing is on it

---

### Post by mmsmc on 2013-05-07
ok. windows recognizes the external hardrive, and I was able to succesfully partition it. Kubunto on the other hand does not recognize it, and will not even open the device through its file system

-update
The error i am recieving when attempting to open the device in kubunto is "error, the kernal driver for this filesystem is unavailible"

---

### Post by fantab on 2013-05-07
If you have any DATA on that USB HDD then I suggest you BACK UP NOW. 
Using your Windows Disk Management Utility DELETE all its Partitions on external USB. And create a new "Partition Table". But DON'T create any partitions yet. Once done.. boot your Kubuntu USB and see if it see the USB. If does then use "TRY KUBUNTU", let the desktop boot and then use GPARTED to create new partions:
30GB ext4 Primary with "/" as mountpoint
2-4GB Primary SWAP.
Reboot and install kubuntu.

---

### Post by mmsmc on 2013-05-07
ok. Gparted is able to detect the external hardrive, and I partitioned them from Gparted. Kubuntu is still unable to open the files under the error that is is not a "valid block device", and therefor is not recognized by the installer

---

### Post by fantab on 2013-05-07
Did the LiveUsb boot to Kubuntu desktop?
Did you create a new partition table? 
Also you cannot install unless you use a mountpoint, "/" on the partition you want to install to.

---

