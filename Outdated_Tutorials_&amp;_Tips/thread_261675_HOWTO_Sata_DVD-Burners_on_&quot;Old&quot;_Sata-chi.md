---
title: "HOWTO: Sata DVD-Burners on &quot;Old&quot; Sata-chipset"
date: 2006-09-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Topfs on 2006-09-20
Hi, I got a few mails this week with the question howto get Sata-DVD burner working on a bit older southbridge chipset. I Have the SH-163a DVD Burner and the i845PE chipset wich means I needed to boot this combo with S-ATA + P-ATA added in bios, this doesn't change anything for windows and it boots but linux on the otherhand stops at Mounting Root Filesystem, though I found out a quick remedy for this problem.

You need to add the startup parameter, irqpoll. This can be done by pressing F6 when you insert your ubuntu CD.
If you already have an installed version of ubuntu you need to add this to the GRUB parameters.

[QUOTE]
sudo gedit /boot/grub/menu.lst
[CODE]

This will open up the config file for your GRUB

Roll down to the following:
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

all you need to do is to change this to

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash irqpoll
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single irqpoll
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

and you are set

This works for me, I have burned DVD's played movies from my CD and have had no problemos, works as perfect with sata.

Hope it helps folks, cya

---

