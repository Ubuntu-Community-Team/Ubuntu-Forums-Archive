---
title: "Help with creating live cd from scratch using Open Suse as a base"
date: 2009-06-18
forum: Programming Talk
---

### Post by climatewarrior on 2009-06-18
I'm attempting to create a simple live cd (no aufs or union fs, no squashfs, not installable) based on a minimal installation of Open Suse. This are the steps I'm taking to create it:

Created the appropriate directory structure... iso/isolinux. Then I made a minimal installation of OpenSuse to a partition. Then Took the initrd and the kernel from the minimal installation and copied them to the isolinux directory. Also I copied over the isolinux binary and made a isolinux.cfg that looks like this:
```
default vmlinuz root=/dev/ram0 initrd=intrdfile
		timeout 1
```
Where vmlinuz is the kernel, and initrdfile is the initrd.

Then I created a file

```
dd if=/dev/zero of=fs.img bs=1024 count=4096
```
(Actually the file was much larger, like 3 gigs)
and associated a loop device with the file (/dev/loop7).  
```
losetup /dev/loop7 fs.img
```
Then I created a file system on it and then I mounted the file system. 
```
mke2fs -F /dev/loop7
mount /dev/loop7 /mnt
```
Then I copied the whole installed file system to this new file system ( I didn't modify anything in the filesystem of the suse minimal install).
```
cp -R /media/minimalInstall/* /mnt
```
After it finished copying I unmount the file system and dissasociated the file from the loop device. Finally a took this file that contains the whole file system and moved it to isolinux. After this I ran mkisofs.
```
mkisofs -R -r -no-emul-boot -b isolinux/isolinux.bin  -boot-load-size 4 -boot-info-table -l  -c isolinux/boot.catalog -o ../bootable.iso .
```
Currently the kernel starts booting up but it says it can't find the device ram0 and drops to a shell, the file system available in the shell is the initrd. Any help or tips would be greatly appreciated. I'm extremely frustrated with this, I've already spent too much time on trying to get it working. 

P.S. I know there are tons of scripts and guis out there to do this automatically, I need to get this working and I can't use any of those tools. This is for a very specific need, also it needs to be Open Suse. I wish it could be Arch, but it is not a choice (not because Arch is lacking something, I just need it to be Open Suse).

---

