---
title: "IBM series X225 server"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by M0pax on 2013-02-16
Hi newby question.
I have got a IBM series X225 server config to raid 5, 3 x36gb SCSI disks. machine was manufactured back in 2003
I installed ubuntu 12.04 32 bit all seamed to be ok got to the end of the install remove cd and reboot.
Server reboots and i just get a blank screen with the curser blinking in the top left corner. I pulled the plug after 10 mins,  booted back of CD and run repair and i got a msg no image on disk?

thanks Graham

---

### Post by cornelis spronk on 2013-02-16
I have the same problem when I tried to install Ubuntu 10.04 two years ago.  I have not come up with any solution partly due to lack of space to experiment.  Ubuntu does not seem to recognize the drives.

I have acquired a PCI IDE hdd controller which I plan to place in a PCI slot and connect it to an old IDE drive. This might at least allow me to use the motherboard.

How to get Ubuntu to address the the SCSI drives through through the back board is beyond me.

Unfortunately I don't have the space to try it.  The computer has been in storage for some time.

---

### Post by M0pax on 2013-02-17
Hi cornelis spronk thanks, do you think you will spend the time to try or more bin food?

---

### Post by cornelis spronk on 2013-02-18
Sorry, no time to try in the near future.

When I purchased the server, I had no idea that the fans would be so noisy, so I am not able to use it in the house.  I purchased it as a spare in case my regular computer, a Dell Dimension 3000 might fail.  On hindsight, it was more of a learning experience than a good purchase.

If you have the time, continue to play with it and report on the forum.  Others might learn from it.  I would be interested.

I downloaded some manuals from IBM, but I have not had an opportunity to search through them for relevant information.

These are the only suggestions I can make.

---

### Post by M0pax on 2013-02-18
I have just found this will have to try soon

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by cornelis spronk on 2013-02-20
I just found this.  A free download.  It might help.

[http://drivers.downloadatoz.com/vendor_ibm_type_bios/326961,ibm-xseries-225-8649-driver-2-02-for-linux/](http://drivers.downloadatoz.com/vendor_ibm_type_bios/326961,ibm-xseries-225-8649-driver-2-02-for-linux/)

---

### Post by DuckHook on 2013-02-20
It is impossible to help with such Spartan information. Please read [sticky]("http://ubuntuforums.org/showthread.php?t=1422475") at top of Absolute Beginners page.

SCSI cards and especially old SCSI cards are problematic in Linux. There are just so darn many of them. I'm not a RAID expert, so don't want to get your hopes up, but more info of the right kind might attract one of the RAID gurus. You might also want to ask the moderators to move this thread into "Server Platforms" where the real RAID gurus frequent.

At a minimum, need output from:```
sudo lshw -sanitize
``````
lspci -vvnn
```If posting in Server Platforms, there's no point if you post without specific HW specs.

---

### Post by cornelis spronk on 2013-02-22
Thank you for the comments on SCSI drives.

This explains to me why I have since picked up a Dell server with a SATA drive and Ubuntu installed perfectly.

---

### Post by M0pax on 2013-02-22
Yes I have given up as well, but I have also used the advanced install and setup raid and it still not working.
I have a new of coming IDE drives

---

### Post by Hydranix on 2013-09-13
You should have set this up in the hardware RAID config option rom. (CTRL + C)

Once the array has been brought up an dis functioning, you need to enter the main system BIOS (F1 at boot)

Under "startup options" change the first boot device to "Hard Disk" or whichever is most similar.

You then need to check that the hard disk boot order is set to boot the array which WILL show up on the list once the array is built.


Ubuntu shouldnt require any special configuration and will treat the disk as any other.


This works on my IBM xSeries 225 with a similar setup.

---

