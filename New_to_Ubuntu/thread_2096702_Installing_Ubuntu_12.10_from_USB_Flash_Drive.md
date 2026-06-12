---
title: "Installing Ubuntu 12.10 from USB Flash Drive"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by ahamza on 2012-12-20
I am trying to install Ubuntu 12.10 from a USB flash drive and was following instructions from Create a USB stick on Windows | Ubuntu to create a bootable USB stick. The errors I get are attached in the images. I would appreciate if someone could tell me what I am doing wrong or not doing. Thanks in advance for your help.[ATTACH]228939[/ATTACH]

[ATTACH]228940[/ATTACH]

---

### Post by odysseusjak on 2012-12-20
I would try using UNetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ahamza on 2012-12-20
> **odysseusjak said:**
> I would try using UNetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I was able to use UNetBootin to create the USB but my BIOS is not recognizing it :confused: What could be doing wrong?

---

### Post by fdrake on 2012-12-20
did you set up the bios to boot from usb. change the order of boot.

---

### Post by ahamza on 2012-12-20
> **fdrake said:**
> did you set up the bios to boot from usb. change the order of boot.

I have set the order to boot from the USB first then my hard drive and when I start my computer it goes directly to windows. 

When I try manually selecting a device from the boot menu one time it doesn't even list the USB there.

---

### Post by oldfred on 2012-12-20
What system and what video card?
Very old system - may not boot from USB.
Very new system - may need secure boot turned off.

Do you get accessibility icons - keyboard & person like shown? 
Press any key to get menu shown in next screen.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by monkeybrain2012 on 2012-12-20
> **ahamza said:**
> I have set the order to boot from the USB first then my hard drive and when I start my computer it goes directly to windows. 

When I try manually selecting a device from the boot menu one time it doesn't even list the USB there.

Some bios seem to be crazy like that, you may need to press Esc or some other keys during boot to boot from the usb even though you have set the order. It is also possible that it doesn't recognize your usb.

---

### Post by ahamza on 2012-12-20
> **oldfred said:**
> What system and what video card?
Very old system - may not boot from USB.
Very new system - may need secure boot turned off.

Do you get accessibility icons - keyboard & person like shown? 
Press any key to get menu shown in next screen.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

AMD A6-3400M APU (6GB RAM - AMD Radeon(TM)HD6520G.

I don't think its a problem with the system's USB booting capability because I was able to run Fedora 17 live image from the same USB a few hours ago. (Bare with me if what I am saying doesn't make sense because I am fairly new to dual-booting/Linux).

I don't get as far as the accessibility options because the system is not even recognizing the USB as a boot option once I have made it into a "Install Ubuntu(I:)".

---

### Post by sandyd on 2012-12-20
Have you checked the MD5SUM of the image?

See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ahamza on 2012-12-20
> **monkeybrain2012 said:**
> Some bios seem to be crazy like that, you may need to press Esc or some other keys during boot to boot from the usb even though you have set the order. It is also possible that it doesn't recognize your usb.

I have eliminated the possibility of it not recognizing my USB since -
1) I have successfully booted fedora live image from the same USB.
2) I have tried booting Ubuntu from a different USB.

---

### Post by ahamza on 2012-12-20
> **sandyd said:**
> Have you checked the MD5SUM of the image?

See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Just checked the MD5SUM via winMd5Sum. They are the same.

---

### Post by fdrake on 2012-12-20
iso is correct & bios is correct ergo ==> usb format/setup is wrong....

---

### Post by oldfred on 2012-12-20
Even flash drives that work on one system, do not always work on others. Not sure if flash drive, BIOS, or how it is installed.

Some get success with one of the other installers, some with other flash drives and others just redo it and it works.

       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by ahamza on 2012-12-21
Yes, I tried to research it as much as I could and then was trying stuff out. Apparently it was the x64 version that wasn't working. The i386 however worked fine. In the end I ended up backing up all my stuff from windows and installing 12.10 on the whole hard drive to give it full resources. But thanks all for the advice and suggestions.

---

### Post by greatsirkain on 2012-12-21
if you're building it in windows format the USB to fat32 then use sardu to create your boot USB, worked for me with 11.04 to 12.04 versions of Ubuntu. You can't set up persistence on the USB with Sardu but it's easy to add extra tools, and recovery options plus multiple live operating systems
[http://www.sarducd.it/](http://www.sarducd.it/)

---

