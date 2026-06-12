---
title: "Booting set up - Ubuntu from USB in Windows 7"
date: 2019-01-08
forum: New to Ubuntu
---

### Post by cassovia on 2019-01-08
Hi Ubuntu experts,
I am about to start UB., 
I´ve created USB flash and at the moment I don´t know how to set up booting source at Bios,
I´m enclosing some photos.

[http://prntscr.com/m4f135](http://prntscr.com/m4f135)
[http://prntscr.com/m4f1kd](http://prntscr.com/m4f1kd)

[IMG]http://prntscr.com/m4f135[/IMG]

[ATTACH=CONFIG]282127[/ATTACH][ATTACH=CONFIG]282128[/ATTACH] 

Thank´s 4 all advices.

& All the best in 2019 everybody!!!

---

### Post by yancek on 2019-01-08
Since there are no universal standards, you will simply have to test the various options.  Some system boards will show the name of the disk in the boot options menu while others will not.  Have you tried the usb-hdd option?  I'd start with that and then check to see if you have anything under the HDD option that points to your usb.  The fact that you have windows 7 installed is completely irrelevant to booting your usb.

---

### Post by oldfred on 2019-01-08
I had a desktop with a Gigabyte motherboard from about 2009 that had all those USB boot options. None of them worked. 
I then tried flash drive in my laptop and it booted as only one USB boot option.

Only by accident did I have flash drive still plugged in and was rebooting system and a "new" drive appeared in the hard drive list.
That BIOS considered bootable flash drives as hard drives and you then get multiple drives to boot from.
So also check that option.

---

### Post by oldrocker99 on 2019-01-08
My own experience has been to boot a USB in "legacy" or "BIOS mode." When I have tried to install in UEFI mode, the installation of grub has failed, leaving an unbootable computer.

Your mileage may vary, but that's been my own experience.

---

### Post by oldfred on 2019-01-08
If system is from 2009, it will be BIOS only.

I never have had an issue with installing in UEFI mode, except the drive location of ESP.
But make sure drives are gpt partitioned, that first drive seen by Ubuntu is gpt with an ESP - efi system partition.
It is only Ubuntu's version of grub that only installs to first drive. I installed Fedora a year or two ago & specified install to sdb drive and it worked. Just tried 19.04 to see if grub any better and it still installed to sda, even though I specified to install grub to ESP on sdb.

---

