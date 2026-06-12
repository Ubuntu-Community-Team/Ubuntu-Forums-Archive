---
title: "Identifying a linux partition"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by archp2009 on 2014-05-21
Is there a simple but sure way to identify the particular linux distribution in a multiboot setup.  I have eight partitions each with a different distro.  Seven of them are Ubuntu derivatives.  The one I can't find (identify with certainty) is Mageia.  I want to edit fstab in that partition as it fails to boot.

---

### Post by oldfred on 2014-05-21
I like to label my partitions, so I know by this which shows labels & UUIDs:

 sudo blkid -c /dev/null -o list

You can see what grub has identified them as, but it does not usually use names:

 List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry

I run BootInfo report from Boot-Repair or just the boot info script which is aout the first third of the BootINfo report.

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But boot files will not tell you which gui you are using as you have same kernel for many flavors.

---

### Post by grahammechanical on 2014-05-21
Doesn't Grub tell you? Grub os-prober makes use of /etc/lsb_release to get information for the menu. Now, in Ubuntu and its flavours lsb-release is not very informative. I will admit that but the different distribution should not have the word Ubuntu in its lsb_release. Providing that different distribution has a file such as lsb_release. This is what lsb_release says for several installs of Utopic Unicorn for Ubuntu and its flavours.

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"


It is possible to edit that file and change "Ubuntu" to Kubuntu, Xubuntu, Lubuntu and so on. Then we do not need to remember what OS we have installed in which partition. We have to run sudo update-grub afterwards from the OS that we use to control the Grub menu.

Regards.

---

