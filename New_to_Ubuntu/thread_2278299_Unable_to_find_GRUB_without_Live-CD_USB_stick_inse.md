---
title: "Unable to find GRUB without Live-CD USB stick inserted"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by Dreaming on 2015-05-15
Hello,

I have recently installed Ubuntu 15.04 x64 via a USB dongle (formatted using rufus usb tool).

The computer has two hard disks, an Intel SSD (sda) and a Western Digital Mechanical disk (sdb). The dongle shows up as sdc when inserted.

Here's the two logs produced by the 'boot-repair' utility - one during the repair, and then after I booted in (with the dongle inserted) I ran another report, so they should be very similar.

Here is the first URL after the repair:

[http://paste.ubuntu.com/11133862/](http://paste.ubuntu.com/11133862/)

Here is a URL after I boot into Ubuntu and run the boot-repair help

[http://paste.ubuntu.com/11133962/](http://paste.ubuntu.com/11133962/)

My suspicion is GRUB is installed on the USB dongle, but boot-repair should surely be able to fix this?

Any suggestions would be great.

Thanks,
Richard

---

### Post by grahammechanical on 2015-05-15
Boot Repair seems to have re-installed Grub into the MBR of all disks. So, if that is the case the Grub boot menu should load without the USB stick being plugged in. 

Have you set the boot system (UEFI/BIOS) to look for an OS on either the SSD or the hard disk? I have found that setting the boot priority is not enough. On my BIOS motherboard I have to set which hard drive to boot from. The BIOS sees a USB stick with an OS on it as an external USB hard disk and ignores the boot priority settings.

Regards.

---

### Post by oldfred on 2015-05-15
Your system promoted flash drive to sdb and made hard drive sdc.

My older BIOS system did the same but changed back when I remove flash drive. It would insert flash drive as sdb after a reboot and sdc & sdd, became sdd & sde. So I had to keep track of which device was which. 
I believe when I installed drives I skipped a SATA port and it loads drives in SATA port order. Not sure quite why flash drive is sde when plugged in, but sdb when rebooting.

---

### Post by Dreaming on 2015-05-22
I found the solution, it was to do with my bios. I turned off fast boot and it worked.

---

