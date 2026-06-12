---
title: "Resizing ubuntu partition ,and removing Mint"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by Polomint01 on 2013-02-26
HI, hope someone can help me.
I have on my sda1 partition Ubuntu 10.10, and on my sda6 Mint.
I want to remove Mint, resize Ubuntu to fill all the space on my HDD, then upgrade to 12.04,using the upgrade option on the 12.04 install CD.

However, I installed Mint after Ubuntu,so its now in position one in my boot order, so worried if I just delete it Ubuntu will not boot up.

I want to remove Mint as I don't need it know,as Ubuntu now has a gnome option.

I have backed up my home drive, and will do a fresh install if all else fails, but would like to try and do it via G parted and  upgrading to see if I can get it to work.

So, at the end of the day, I am aiming for just having Ubuntu 12.04 (will use the old skool classic gnome once installed). and hopefully all my applications and files as intact and working as possible.

I have googled, but am a little confused.

Any help welcome.

See attached files of a screen shot of my drives at the present.

---

### Post by oldfred on 2013-02-26
You need to install grub to MBR from Ubuntu first. Then from LiveCD and with swap off you can edit partitions. You can not use working install, as partitions are mounted and you cannot edit mounted partitions.

You might want to think about some more changes, if you may want to install other systems to test. I like to have more than one install and experiment on the other install but keep one I know works. A good way to test a new version.

I then only use 25GB for / (root) and have all data in separate data partitions that I can mount in any install. I do not attempt to share a /home as then settings from one system may conflict with another.

Boot into Ubuntu and run this:
       sudo grub-install /dev/sda
sudo update-grub

---

### Post by Polomint01 on 2013-02-27
Hi Thanks for the commands to make Ubuntu boot first.

However,I am not sure what to do next,I swapped off, but cannot still resize my Ubuntu partition .The extended partition sda2 will not shrink down, to allow me to enlarge sda1 containing my Ubuntu install.

Thanks again for your help.

---

### Post by plucky on 2013-02-27
> **Polomint01 said:**
> Hi Thanks for the commands to make Ubuntu boot first.

However,I am not sure what to do next,I swapped off, but cannot still resize my Ubuntu partition .The extended partition sda2 will not shrink down, to allow me to enlarge sda1 containing my Ubuntu install.

Thanks again for your help.

Have you deleted sda6?

sda2 will not shrink if sda6 is still there.

Good Luck

---

### Post by oldfred on 2013-02-27
The extended partition sda2 is the container for all the logicals. So what is inside has to be changed first.

You have to shrink or delete the logical partitions and only then can you resize the extended partition.

---

### Post by Polomint01 on 2013-03-02
Just let you all know, have now upgraded 10.10 to 12.04, via the 12.04 live CD, was nervous, but all went well, lost some applications.

---

