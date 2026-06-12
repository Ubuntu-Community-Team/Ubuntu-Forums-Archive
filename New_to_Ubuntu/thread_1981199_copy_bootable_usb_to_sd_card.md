---
title: "copy bootable usb to sd card"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by cleeve51 on 2012-05-16
I have created a bootable USB so I have dual boot option on eee pc. However, I want to boot from the SD card instead of the USB. I've tried, and failed, to copy the OS and now the SD card probably needs a re-format. 

I'm sure it must have been asked before and I have searched and failed to find the answer.

Please can someone tell me the commands to format the SD & to copy the OS from the USB to the SD.

---

### Post by philinux on 2012-05-16
> **cleeve51 said:**
> I have created a bootable USB so I have dual boot option on eee pc. However, I want to boot from the SD card instead of the USB. I've tried, and failed, to copy the OS and now the SD card probably needs a re-format. 

I'm sure it must have been asked before and I have searched and failed to find the answer.

Please can someone tell me the commands to format the SD & to copy the OS from the USB to the SD.

I think you need to put the sd card into an external USB card reader then use the startup disk creator and point it to the device.

---

### Post by sudodus on 2012-05-16
If the size of the flash card is at least big enough for the used part of USB drive (the partitions), you can probably use dd. It is nick-named disk-destroyer, because it does what you tell it to do, and does not ask if that is really what you want ;-)

If you are really careful and check the device names of the two drives, and get the input and output devices right, it does magic :KS

For example, if you have one HDD, and insert the USB drive first and the flash card after the USB drive is recognized, it should be like this

/dev/sda -- internal HDD
/dev/sdb -- USB drive
/dev/sdc -- flash drive

(but check this with
```
sudo fdisk -lu
``` and ```
sudo blkid
```
to be sure and [COLOR="red"]edit x and y[/COLOR] to fix your device names before you run the command!!! Maybe x --> b and y --> c but maybe not, you must check it yourself.)

and your command line will be
```
sudo dd if=/dev/sd[COLOR="Red"]x[/COLOR] of=/dev/sd[COLOR="red"]y[/COLOR] bs=4096
```
You get no output during the process and the speed is not very high via USB, so you have to have patience ...

---

### Post by westie457 on 2012-05-16
+1 to what philinux said.

The in-built SD card reader is usually not recognized by the BIOS at boot time. Also Grub does not pick up an ISO file on a SD card in the reader so you cannot try to boot it that way either.

---

### Post by sudodus on 2012-05-16
You can boot an eee pc from the built in flash card drive, at least older models.

[[COLOR="Red"]_http://www.ehow.com/how_6953228_boot-eee-pc-sd-slot.html_[/COLOR]]("http://www.ehow.com/how_6953228_boot-eee-pc-sd-slot.html")

And if you feel scary with dd, please do the boot drive creation procedure once more (pointing directly to the flash drive)!

Good luck!

---

### Post by cleeve51 on 2012-05-16
Solved
Thanks to everyone, I'm sure all methods work but I used Sudodus' dd commands and it worked perfectly.

---

### Post by sudodus on 2012-05-17
I'm glad it worked for you. Please click on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page to mark this thread as SOLVED.

---

