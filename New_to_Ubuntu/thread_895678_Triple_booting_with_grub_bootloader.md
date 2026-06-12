---
title: "Triple booting with grub bootloader"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by wesley_snipes on 2008-08-20
I plan to attempt a triple boot with Windows Vista, Windows XP and Linux Ubuntu. With Vista already installed, I plan to install XP next, then Ubuntu. I know that Easy BCD can boot the three OS's, and grub can dual-boot either XP or Vista with Ubuntu, but I would like to know if it is possible to triple boot using grub, rather than installing Easy BCD.

Has anyone had success triple booting with grub? Thanks.

---

### Post by bobnutfield on 2008-08-20
I don't much about Vista, but I can tell that Grub will load different flavors of Windows.  They have their own boot loader, so you would chainload them on their respective partitions.  An example of a Grub entry of this type is:

title WinXP
root (hd0,0)
rootnoverify
makeactive
chainloader +1

I used to boot XP and Win98 in this manner, and I assume it would work for Vista as well.

Have a look at this:

[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php]("http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php")

---

### Post by Gone fishing on 2008-08-20
I triple boot - however, I don't use grub for triple booting I load grub onto the Linux partition and then use the GAG boot loader which is very easy to configure.   

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

