---
title: "GParted partition mount help"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by r2apshktz on 2008-10-31
OK So I had a dual booted HDD with Ubuntu and WinXP. I wanted to return the HDD to full XP usage. I used GParted to delete the ext3 files and such. And expand the Windows partition. When I tried to reboot into windows all I get some text about Grub loading error.

The ntfs boot partition is not mounted. How can I mount it? Will that solve my problem? What else can I do?

Please help me:(

---

### Post by Coreigh on 2008-10-31
I believe there is a way to fix this with an Ubuntu LiveCD, but I don't know how. I have always had to fall back on good (bad?) old MS-DOS and fdisk /MBR.

I still have a win98 emergency floppy I can boot with (I have a CD version too) it boots to MS-DOS command line and then I type```
fdisk /MBR
``` this will rewrite the Windows master boot record, overwriting Grub.

This like everything is not without risks, but it has worked well for me many times.

Hopefully someone will post instructions on how to restore Windows MBR using the LiveCD, Or a Windows install CD, because floppies are dead dude.

---

### Post by overdrank on 2008-10-31
> **r2apshktz said:**
> OK So I had a dual booted HDD with Ubuntu and WinXP. I wanted to return the HDD to full XP usage. I used GParted to delete the ext3 files and such. And expand the Windows partition. When I tried to reboot into windows all I get some text about Grub loading error.

The ntfs boot partition is not mounted. How can I mount it? Will that solve my problem? What else can I do?

Please help me:(

Hi and you will have to restore the MBR and this link may help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Edit to slow :)

---

### Post by r2apshktz on 2008-10-31
Thank you both. I'll try that.

---

### Post by r2apshktz on 2008-10-31
Overdrank, You are my hero.
I was really stumped.
That SGD worked wonders. Thanks a million.

---

