---
title: "multi-boot grub problem"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by crip720 on 2013-02-26
Hi, I installed Fedora 16 and it messed up grub on sda.  Use grub on sdb and booted to Ubuntu 10.04.  Did sudo update-grub and found all the OSs on my partitions, plus Fedora.  Shut down and restarted, but grub came on, but only with Ubuntu 10.04w/recovery/memtest and Windows 7.  Booted to 10.04 ran update-grub and update burg, same thing.  Ran Boot-repair[paste.ubuntu.com/5563774]  same thing happen.  So now instead a multi-boot, I only have a dual-boot laptop.  Can anyone help,  Boot-repair does not list boot type for the missing OSs.  I know that a couple of the partitions have grub-config problems that I caused, but the others are okay.  Fedora was replacing one.  Thank you, Colin.

---

### Post by PunkLV on 2013-02-26
From Live Session:
```
sudo apt-get install os-prober
```
Mount all your partitions. Run os-prober. Install grub on the sdX, make sure sdX is the primary boot device in BIOS.

---

### Post by crip720 on 2013-02-26
Thanks, will try it tonight.

---

### Post by ajgreeny on 2013-02-26
If you used the default fedora installation it will have used LVM partitions which ubuntu can not deal with unless you install the various LVM packages.  I run 10.04 still and in that it needs lvm2 plus dependencies. Search for lvm in software centre or synaptic if you use that and see if that helps your grub find fedora.

---

### Post by crip720 on 2013-02-26
update-grub finds all of the OSs, but the grub screen to choose is only showing 10.04 on sdb5 and windows7 on sda2.  os-prober did not help.  Colin

---

