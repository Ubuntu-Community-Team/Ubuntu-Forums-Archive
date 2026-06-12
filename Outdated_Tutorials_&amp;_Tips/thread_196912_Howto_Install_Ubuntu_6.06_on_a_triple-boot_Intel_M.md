---
title: "Howto: Install Ubuntu 6.06 on a triple-boot Intel Mac"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by thephotoman on 2006-06-14
Okay, so you've got a Macbook, and you don't want to shell out for Parallels--you want to triple boot it.  Well, in addition to following the instructions [here]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp"), you've probably going to want to make some adjustments to that guide, particularly in regard to the Ubuntu install.  It's probably not the best idea to bootstrap Ubuntu, though I guess you could if you were knowledgable enough.  However, I didn't feel like doing that.

To be completely honest, I got this mostly from [here]("http://bin-false.org/?p=17")

I'm not going to go over the stuff on BootCamp.  That's posted at the Wiki link above.  This is only on the Ubuntu install.

This doesn't work with the Alternate CD--you need the abiltiy to open a shell and a text editor at the same time to do it.

So, the first step is to go in and edit the partition table.  You've got to do this before running the installer, because you're going to need to make a swap file before you begin installing, or else the installer will hang.

So, pop open a terminal and issue the following commands:

sudo parted
mklabel Ubuntu
print
mkpart primary ext3 32kb [size of hard drive]
exit
sudo mkdir /mnt/linux && mount -t ext3 /dev/sda3 /mnt/linux
sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
sudo mkswap /mnt/linux/swap
sudo swapon /mnt/linux/swap

Now, you can start the installation.  Once you get to the partitioner, select "Manually edit partition table", and then skip over the next screen.

On that screen, mount / on sda1.  Make sure that the box to format the disk is UNCHECKED.  This is necessary because you don't want to destroy that swap partition you created.  Then, finish the installation as usual, but don't reboot yet, as you're not done.

After the installation is finished, you need to go into a terminal again and issue the following commands:

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda3 /mnt/ubuntu/
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash
apt-get install lilo lilo doc
apt-get remove grub
gedit /etc/lilo.conf

Make that file look like this:

boot=/dev/[linux-partition]
default=Ubuntu

map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/[linux-partition]
label=Ubuntu
read-only

Then, in a new terminal (without chroot), run the following commands:

sudo parted
print
set [insert Linux partition here]
boot
on
quit
exit

Then, back in the chroot terminal, issue the following command:
lilo -b /dev/[insert drive here]

If this works, you're all good.  Close the chroot window, and unmount /mnt/ubuntu/dev, /mnt/ubuntu/proc, and /mnt/ubuntu.  Now, you can restart the computer.

---

### Post by chaosfiredragoon on 2007-02-23
so at the end i should just open a new terminal and type unmount?

---

### Post by xfile087 on 2007-02-23
> **chaosfiredragoon said:**
> so at the end i should just open a new terminal and type unmount?

I'm probably wrong not doing so but I don't even bother unmounting I just do a "sudo reboot". Not had any problems myself but I have a feeling I really should unmount first!

---

