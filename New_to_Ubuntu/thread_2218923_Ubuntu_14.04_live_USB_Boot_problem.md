---
title: "Ubuntu 14.04 live USB Boot problem"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by upsla on 2014-04-22
Hi All
 I recently downloaded Ubuntu 14.04-32 bit iso from official source. I tried to install it to my computer by using **Unebootin**. But after the whole process when I tried to boot the usb I am stuck with syslinux screen forever. Any suggestions folks.

---

### Post by oldfred on 2014-04-22
What computer? Model & video chip/card model.

If a newer computer with 2GB or more of RAM the 64 bit version probably would be better.

If a really old computer, you may need Lubuntu or perhaps Kubuntu. 

You can verify that download is correct:
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by C.S.Cameron on 2014-04-22
UNetbootin sometimes lags Ubuntu, try Startup Disk Creator from the Live DVD.

---

### Post by upsla on 2014-04-23
My Computer has  2GB RAM,NVIDIA Geforce 8500GT graphics card. I running ubuntu 12.04 LTS 32 bit alongside with Windows 7.

---

### Post by upsla on 2014-04-23
Tried that too. Atleast UneBootin will take syslinux page, but with Ubuntu startup disk creator, it shows BOOT error.

---

### Post by oldfred on 2014-04-23
I have a slightly newer nVidia and have to always add nomodeset on live installer boot and first boot after install or until I install the proprietary driver.

 To install Ubuntu, boot from the DVD press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.

        How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

After install:

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

