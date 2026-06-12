---
title: "Can I do this?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Kdawkins on 2008-07-06
Hey all,

This is how I set up my Hard-Drives:
3 X (500 Gig) in RAID-5 (software, via nforce mobo) ---> Windows Vista
1 X (500 Gig) separate from the RAID array ---> Planned for Ubuntu 8.04

If I install Ubuntu on that drive, will it mess up my whole windows booter? Basically I am asking if grub can boot to windows on a RAID or do I have to use supergrub to restore windows MBR? My first priority is making sure windows works, its what my family uses.... :-( 


Thanks,
Kevin

---

### Post by logos34 on 2008-07-06
Play it safe and install grub to the MBR of the ubuntu drive.  Then just toggle the Bios hard disk boot order whenever you want to boot into linux.

On the Hardy 8.04 live cd you'll come to a screen "Ready to Install'. Click on 'Advanced' button lower-right and change the Grub default location '(hd0)' to '/dev/sdd' or whatever the ubuntu drive is seen as.

---

### Post by red_team316 on 2008-07-06
like logos34 said, you have to tell grub which hard drive to install to. By default, it installs on the first hard drive(sda) which is apparently your windows drive. Instead of toggling the bios whenever you want to boot to linux, make your ubuntu drive the first to boot in the bios as well as have it hooked up to the SATA1 port on your mobo, and then when you install ubuntu, it will recognize that windows is on your other drives and should create a menu option for it, thus eliminating having to change boot order.

---

### Post by logos34 on 2008-07-07
> **red_team316 said:**
>  it will recognize that windows is on your other drives and should create a menu option for it, thus eliminating having to change boot order.

yep, forgot to add that part...But whether that entry will successfully boot a vista raid (5, no less) array is another matter.  It would be nice if works without further ado

---

