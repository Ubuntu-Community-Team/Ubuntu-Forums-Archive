---
title: "Unable to load custom compiled vmlinux - please help"
date: 2010-10-31
forum: Packaging and Compiling Programs
---

### Post by ak71 on 2010-10-31
I downloaded the source code, compiled it and copied vmlinux to /boot directory. I then ran update-grub (I have the version 2.6.35.22 with grub 2 on it).

When I shutdown and restarted on the virtualbox, I got an error that said

error invalid magic number 
failed to boot both default and fallback entries
Press any key to continue

It was stuck at this point and kept giving this message repeatedly. My only solution was to restore a backup of a .vdi file in the HardDisk directory of the Virtualbox.

More details on what I did.

I installed Oracle VM VirtualBox on my Mac laptop. I installed Ubuntu and downloaded the source code and ran the following command.

cd linux-2.6.35
sudo make menuconfig
sudo make

This created a file called vmlinux. I renamed this vmlinux-1 and copied this over to /boot.

I then opened /etc/grub.d/40_custom and added the lines starting from menuentry till the end of the closing brace:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Custom Linux" {
set root=(hd0,1)
linux /boot/vmlinux-1
initrd /boot/initrd.img-2.6.35-22-generic
}


I then ran update-grub and restarted and I ran into the problem described above. 

What am I doing wrong? Also, is the 40_custom file correct? What is initrd? I just filled in the named of the file I found in /boot. Also, is (hd0,1) the correct value in the first line of the menuentry?

Am I missing any steps or am I entering some erroneous information? Any help will be greatly appreciated. I have already read the Grub 2 tutorial and I simply followed the steps listed there.

Please help. Thanks in advance!

---

