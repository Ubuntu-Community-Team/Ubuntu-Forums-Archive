---
title: "Dualboot Ubuntu 12.04 and Windows 7 issues"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by trungNguyen on 2012-04-15
I got the problem after install ubuntu 12.04 to window7.
The boot screen does not show the option to select window7 or ubuntu. I did try to delete partition and reinstall ubuntu with the first option dual boot the unable to boot the machine one the installation complete. Is any one help me to edit the boot sector to include the ubuntu boot option?

Thanks

Trung Nguyen

---

### Post by oldfred on 2012-04-15
Welcome to the forums.

Your issue is different than the thread you posted in. Please start new threads when the issue is different. Moved to its own thread.

From liveCD or USB download and run the boot info script from this. You also can down it as a full ISO to boot separately. We would prefer to see the result the script creates so we can suggest repairs.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by ogoforth on 2012-04-28
Have windows 7 Ultimate 64 bit.  After installing Ubuntu 12.04 to dual boot, grub seems to not be loading.  Machine boots right into Windows.  The install of Ubuntu has created the appropriate partitions.  Can't boot to the Ubuntu install.:confused:

---

### Post by bennachie on 2012-04-28
@ogoforth

You could try relaunching your liveCD, opening a terminal window, then typing the following commands:

sudo fdisk -l

That should show you the actual partitions on your disk, and you should be able to identify the "/" partition for Ubuntu. You can then, in sequence, type the following commands:

sudo mkdir /media/sdax	[where &#8220;x&#8221; is the / partition for Ubuntu]
sudo mount /dev/sdax /media/sdax
sudo grub-install &#8211;root-directory=/media/sdax /dev/sda
exit

Exit from the LiveCD, remove the CD or USB stick and restart. You should be able to choose to boot from either Ubuntu or Windows. If you have a straightforward dual-boot installation, that should be enough, but it would do no harm to open a terminal window, and run:

sudo update-grub

just to confirm that both operating systems are being properly recognised.

Good luck.

---

