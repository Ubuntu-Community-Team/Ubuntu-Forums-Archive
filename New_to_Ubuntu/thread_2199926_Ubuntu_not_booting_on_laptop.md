---
title: "Ubuntu not booting on laptop"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by david131 on 2014-01-16
Recently installed ubuntu on my Compaq Presario Desktop. 32 bit.

This was a complete install of ubuntu. No other OS is running.

ubuntu will not boot.  I use boot repair, still will not work. All I see is a mauve screen,

I ran the Recommended Repair and this is the link it  generated: [http://paste.ubuntu.com/6754083/](http://paste.ubuntu.com/6754083/)

I will appreciate any help I can get. Thanks.

---

### Post by TheFu on 2014-01-16
There seem to be lots of I/O errors related to the HDD in the system. Could be
[LIST]
[*]bad cable
[*]bad disk controller
[*]failing HDD
[*]cracked motherboard
[*]failing power supply
[/LIST]

---

### Post by oldfred on 2014-01-16
Top of boot script shows it cannot mount partitions, and grub reinstall has same issue.
>  Invalid MBR Signature found.



But then it shows partitions with fdisk, parted and blkid???

What does drive show in Smart Status? Use disks or disk utility and click on drive. It can show lots of detail on drive, but all I know is passed is good.

Post this.
sudo hexdump -n512 -C /dev/sda

---

### Post by king.of.random on 2014-01-16
Does your laptop work using the live disc? This could rule out hardware issues. The mbr issues are strange.... How old is your hard drive? It may be failing. Also can you run memtest from grub? let it run a an hour or so as it will certainly show up memory issues and maybe a failing motherboard. Can't remember if gparted is on the live disc, I think it is, but if not install and run this it maybe that you need to reformat and reinstall... it is a really good gui partitioner, making things easier to understand what you're doing; I use it all the time when multi booting.

---

### Post by zircon_34 on 2014-01-17
I had that problem with an acer aspire few years ago. To be able to boot into linux I had to turn acpi off or noapic, thats something in the bios boot menu. I found [a thread]("http://askubuntu.com/questions/52096/what-do-the-different-boot-options-mean-i-e-acpi-off-noapic-nolapic-etc") explaining a little bit about that, maybe this could help.

---

