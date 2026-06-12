---
title: "installation problem : ubuntu server 22.04 to ssd"
date: 2023-04-04
forum: New to Ubuntu
---

### Post by joeythedream on 2023-04-04
Hiya, ubuntu server installation to Raspberry Pi4B ssd failure.

A Samsung 2T SSD (870 QVO V-NAND SSD) is purchased for my Raspberry Pi4B as replacement of SD-card.


Before burnt imager (by my laptop windows11) into my ssd, 

I follow the below website (case 2) to "showing up" my ssd in windows 11 as
 
[https://www.easeus.com/storage-media-recovery/ssd-not-showing-up-windows-10.html](https://www.easeus.com/storage-media-recovery/ssd-not-showing-up-windows-10.html)


Then I follow the below website to prepare a sd-card and my ssd
[how-to-boot-raspberry-pi-ssd-permanent-storage]("https://www.makeuseof.com/how-to-boot-raspberry-pi-ssd-permanent-storage/") 

1.  imager "usb boot" to sd-card => insert RPi to green screen, switch off, take out the sd-card
2.  imager "ubuntu server 22.04, 64bit" to ssd
3.  connect the imaged ssd into RPi thru' "SATA2.5inch-USB" cable to usb3 socket of USB, power on the RPi

I did it thrice but all failed, but with different error each time :

some type here ;
[FAILED] Failed to stat Flush Journal to Persistent Storage
[FAILED] Failed to start Device-Mapper Mutipath Device Controller
[FAILED] Failed to start Create System User

The Rpi4B is work properly with sd-card, and any command from you ?

Thank you very much

---

### Post by MAFoElffen on 2023-04-04
I don't know... I did this over a year ago, and followed some more detailed instructions where I had to do a lot of things manually. I failed at first, because the firmware that the board came with, was before it supported booting from USB...

Before I could do *anything*, I first had to update the firmware on my Raspberry Pi4 to the latest firmware, so it could support booting from USB...
```

sudo apt install -y rpi-eeprom
sudo rpi-eeprom-update  # Check to see if there is a newer update
sudo rpi-eeprom-update -a  # Upgrade the firmware
sudo reboot

```
Then I could follow a tutorial to change the boot sequence, and to transfer the OS to, (what I did) an NVMe drive in a USB enclosure.

---

