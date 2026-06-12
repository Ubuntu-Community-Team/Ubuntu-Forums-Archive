---
title: "repartioning hard drive and cleaning up system for a dell inspiron 1501"
date: 2014-11-13
forum: New to Ubuntu
---

### Post by daveritah on 2014-11-13
I am new to Ubuntu and have a Dell Inspiron 1501 with a 80 gb hard drive. I have previously partitioned the hard drive to boot up either Ubuntu or my Microsoft Windows XP using GRUB. I have EaseUS as a partitioning tool (home edition). I want to clean up the hard drive by deleting my old Ubuntu Linux 2.6.31-14 generic (on/dev/sda5) from the drive with its swap files and all, leaving only my Windows XP Home Edition (on/dev/sda1) and my Ubuntu with Linux 2.6.32-21 generic on the drive. ?- How do I delete the Ubuntu Linux 2.6.31-14 off of the hard drive and remove it from my GRUB as well. 2nly, how do repartition the hard drive so that my Windows Xp gets 60 gb and my Ubuntu with Linux 2.6.32-21 has 20 gb of space on the hard drive. and lastly, how do upgrade the Ubuntu 2.6.32-21 to the current edition without creating another mess as I have done in the past and wind up with 2 Ubuntu's on the same hard drive taking up space along with my Windows. I am new to partitioning tools and still learning how to effectively use them, so any help here would be greatly appreciated.

---

### Post by ibjsb4 on 2014-11-13
The 2.6 kernel.  You must be running 10o4.  You would have to upgrade from that to 12o4 to 14o4.

You could probably get away with the 12o4 upgrade; it has a 2d version of unity and will usually run on older equipment.  But 14o4 does not have the option and this will likely break your box.

I think you should look at other options.  Maybe Linux Mate or Xubuntu or Lu.

[http://ubuntuforums.org/showthread.php?t=2241326](http://ubuntuforums.org/showthread.php?t=2241326)

About grub.  You mention removing old kernels, but do you have just one install of ubuntu (sda5)?

Maybe post a pic of your partition layout and what are your computer specs.

---

### Post by grahammechanical on 2014-11-13
We need to be clear about the partition layout. Please correct if this is wrong.

sda1 = Windows XP
sda5 = Ubuntu + Linux 2.6.31-14 that is no longer needed.
sda? = What partition is Ubuntu + Linux 2.6.32-21 on?

What other partitions do you have? Did you really install another version of Ubuntu? When an installation of Ubuntu gets an upgrade to the kernel such as going from Linux 2.6.31-14 to Linux 2.6.32-21 the previous kernels are not removed and we can load them from the Grub menu. That does not mean that they are on a separate partition.

But If we use the Install Alongside option to install Ubuntu alongside XP and then we use the Install Alongside option a second time with a newer version of Ubuntu then we truly get 2 versions of Ubuntu each in its own partition. We need to be clear about the situation before we offer advice.

Your machine has a 80GB hard drive and that makes me wonder about the rest of the hardware whether it can run the latest versions of Ubuntu or whether it would be better to install one of the flavours of Ubuntu. Please provide details about the CPU, the amount of system memory (RAM) and the graphic adapter and the amount of memory that it has. 

Please run a Ubuntu live session and open a utility called Gparted and take a screenshot of your partition layout and post it here.

Assuming that you do have different installs of Ubuntu on different partitions then my suggestion would be

1) To use Gparted to delete one of the Ubuntu partitions. This would create unallocated space.
2) Use Gparted to move and shrink/expand as neccessary the other Ubuntu partition to move the unallocated space up to the XP partition.
3) Use a Windows utility to defragment Windows and do it at least twice making sure that XP loads each time.
4) Use a Windows utility to expand the XP partition into the unallocated space.
5) Forget about upgrading Ubuntu to a newer version. Install a newer version of Ubuntu or a Ubuntu flavour onto the present (remaining) Ubuntu partition using the Something Else option. A new install will make use of the existing swap partition. 

I hope that you have backed up all your data in both Windows and Ubuntu. I have given you an outline plan of how I would handle this. Detailed instructions can come once we have a clearer understanding of your partition layout and how you want to do this.

Regards.

---

