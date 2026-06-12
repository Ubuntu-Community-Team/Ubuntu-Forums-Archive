---
title: "Grub compile problem (no prefix)"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by halikus on 2013-03-22
Hi all.   I have been trying to make a self contained grub.efi image (all modules).  I was intending on using it on my all in one usb.  The usb boots fine with rEFIt and works with other grub.efi files, but not the ones i compile.  It allways complains about prefix not found no matter how i compile it.  Im sure im doing something wrong that is easily overlooked, and am a *nix amateur.  

 I installed Ubuntu 12.10 x64 in Vmware in EFI mode.  To do this, i setup the vmx, and then edited it with notepad and put 
firmware= "efi"
in the second line.  It installs fine.  Then i did apt-get update, and then went to update manager, updated the rest, and rebooted.

Then, assuming my usb is dev/sdb1, and my username is halikus, i do the following:

apt-get install gcc flex bison flex binutils gettext make python autoconf automake autogen grub-common libdevmapper-dev lsb-base libfuse2 zfs-fuse fuse-zip libfuse2 grub-common grub-efi-amd64

#download and extract grub-2.00 to desktop
cd /home/halikus/Desktop/grub-2.00
./configure --with-platform=efi --target=x86_64 
make
cd /home/halikus/Desktop/grub-2.00/grub-core
../grub-mkimage -d . -o grub2x64.efi -O x86_64-efi -p "" `find *.mod | xargs | sed -e 's/.mod//g'`

The image is compiled in grub-core, but when i try it in my usb it allways says prefix not found and goes to the command line.

I have seen other documentation with setting the prefix like
./configure --prefix=/efi/grub --with-platform=efi --target=x86_64 --program-prefix="" 
and
../grub-mkimage -d . -o grub2x64.efi -O x86_64-efi -p /efi/grub `find *.mod | xargs | sed -e 's/.mod//g'`

but they have the same error.  I have a grub.conf in the same directory as the .efi files in efi\grub\ , which is where i would prefer the files to reside.  I am fine with them anywhere within the efi directory.  I had read by leaving the prefix blank with -p "" would have it search for the grub.conf in the same directory as the efi files, but it still doesn't work.

Can anyone see the error of my ways and help a beginner out?

---

