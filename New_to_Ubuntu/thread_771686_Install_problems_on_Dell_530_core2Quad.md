---
title: "Install problems on Dell 530 core2Quad"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by darkwalk on 2008-04-27
Hi all: I'm having a hell of a time trying to install Ubuntu. Been trying for 4 hours now so I thought I'd ask for some help here. Thanks in advance!

My Partitions:
Hd0 pri1 1gig swap
Hd0 pri2 12gig Ext3  (where I'm mounting root (/))
Hd0 pri3 25gig NTFS  (Xp pro)
Hd0 ext 

1st try: 8.04 64bit server edition
Installed OK. Grub detected my Xp installation. Tried to boot Ubuntu, but gives me fatal error (didn't write it down). Tried to boot windows afterwards, but grub changed something and now xp will not boot. Reimage and install XOSL boot loader and Xp works again.

2nd try: 8.04 32bit server edition  (downloaded from MIT mirror)
3rd try: 8.04 32bit desktop edition (downloaded from MIT mirror)
4th try: 7.10 32bit server edition  (from torrent)
5th try: 7.10 32bit server edition  (from torrent)

2nd to 5th try no luck installing. Gives me a "Debootstrap warning" first, then and error stating "unable to install busybox-initramfs".

At this point, I'm about to give up. Can anyone give me suggestions on what I'm doing wrong? Thanks!

---

### Post by srijai on 2008-10-01
I am having the problem of 'Debootstrap Warning - Unable to install busybox-Initramfs'. I am try install hardy server-amd64 version 8.04-1 on a AMD64 desktop with IDE HDD and ASUS Motherboard with NVIDIA Chipset. The download went fine and the MD5Checksum is ok. The CD Integrity check after burning the iso also is fine.

Can anybody help?

---

