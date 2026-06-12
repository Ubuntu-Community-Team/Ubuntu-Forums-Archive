---
title: "Can't read any CDs or DVDs"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Endlessly on 2011-11-30
Hi,  I am trying to read some data CDs and DVDs but Ubuntu isn't detecting them for some reason. I am using known good media (works on other machine which is also using Ubuntu).

Ubuntu does recognise there is a drive, and I can boot from a live CD, so I know the drive isn't broken.  

When I use lshw, I get the hard drive and: 

*-cdrom
       description: DVD-RAM writer
       product: DVD+-RW DH-16AAS
       vendor: PLDS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/dvdrw2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JD12
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2

This system is a Dell Optiplex 780 (if that's any relevance).  Can anyone help, please?

---

### Post by lechien73 on 2011-11-30
Hi & welcome to the forums,

Just a couple of questions first - is this a new installation of Ubuntu, or is it an upgrade?

I seem to recall reading before that if your CD-ROM drive is listed before the hard disk drive in your BIOS boot order, then this can cause problems. You might want to go into BIOS and adjust the boot order.

Additionally, could you please post the contents of your /etc/fstab file?

Thanks

---

