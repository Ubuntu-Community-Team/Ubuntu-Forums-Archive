---
title: "Cannot boot to Ubuntu. Tested 2 USB pendrives. Blinking/flashing cursor on screen."
date: 2014-02-14
forum: New to Ubuntu
---

### Post by phemt2 on 2014-02-14
I'm currently trying to boot into an asus eeepc as it can't boot into windows.

"*Reboot and Select proper Boot device* or Insert Boot Media in selected Boot device and press a key" is the message I'm getting, which is of course what prompted me to try Ubuntu to try to recover some data.

As the topic says, I've tried 2 USB pendrives. A 8GB Corsair one, and an 8GB PNY one. unetbootin for installation. 

I have of course configured the bios/boot device correctly or alternatively chose to boot directly from the usb but to no avail.

I've seen the thread where people confirmed that certain USB pendrives don't work for some reason, but for 2 of them not to work? That makes me think it's not the pendrives at all.

Am I doing something wrong? Or is some hardware preventing it from booting up, if that's possible?

---

### Post by oldfred on 2014-02-14
Often a video driver issue. 
Have you tried nomodeset?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

But some Gigabyte motherboards will only boot from flash drivers that are 4GB or less unless you update BIOS/UEFI.

---

### Post by phemt2 on 2014-02-14
I don't think it's a video driver issue. This is an ASUS Eee PC 1001p Netbook with an integrated graphics card. Here are the specs: [http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_1001P_Seashell/#specifications](http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_1001P_Seashell/#specifications)

 Either way I can't try it because I can't get past the blinking cursor screen.

I don't know if the 4gb limit still applies despite not having a Gigabyte motherboard.

---

### Post by Matthew_Smith on 2014-02-14
Have you made the pendrives bootable? If not, go into "cmd" (command prompt) and type in DISKPART > LIST DISK > SELECT DISK [the number of your pendrive] > CLEAN > CREATE PARTITION PRIMARY > SELECT PARTITION 1 > ACTIVE > FORMAT FS=NTFS > ASSIGN > EXIT

More on that here: [http://www.computerhope.com/issues/ch001366.htm](http://www.computerhope.com/issues/ch001366.htm)

Thanks,
Matthew Smith

---

### Post by phemt2 on 2014-02-14
> **Matthew_Smith said:**
> Have you made the pendrives bootable? If not, go into "cmd" (command prompt) and type in DISKPART > LIST DISK > SELECT DISK [the number of your pendrive] > CLEAN > CREATE PARTITION PRIMARY > SELECT PARTITION 1 > ACTIVE > FORMAT FS=NTFS > ASSIGN > EXIT

More on that here: [http://www.computerhope.com/issues/ch001366.htm](http://www.computerhope.com/issues/ch001366.htm)

Thanks,
Matthew Smith

I'm on a Macbook Pro. Isn't unetbootin supposed to do just that, make them bootable?

Should I do it manually as instructed here? [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

Although those are instructions to boot on a Mac, so probably not.

---

### Post by Gordonbp531 on 2014-02-14
It could be that the iso you downloaded to create the bootable drive is corrupted. Did you check its MD5 # first?

---

### Post by phemt2 on 2014-02-14
I don't think that's possible. I downloaded the 32 bit version of Ubuntu twice and both installations on both USB pendrives installed without a hitch.

---

### Post by Gordonbp531 on 2014-02-15
Do you get the initial Grub screen with options like "Try Ubuntu without installing" and "Install Ubuntu" etc etc, or doesn't it even get that far?
Do you have access to another computer you could try the pendrives on?

---

### Post by phemt2 on 2014-02-15
> **gendibal said:**
> Do you get the initial Grub screen with options like "Try Ubuntu without installing" and "Install Ubuntu" etc etc, or doesn't it even get that far?
Do you have access to another computer you could try the pendrives on?

No like I said, I can't get past the blinking cursor screen. If I stick a pendrive in one of the USB slots I get the blinking cursor on screen. Without any USB drives attached I get "*Reboot and Select proper Boot device* or Insert Boot Media in selected Boot device and press a key".

Is everything correct/as it should be?

[IMG]http://i.imgur.com/qXdYzlu.png[/IMG]

---

### Post by bookrt on 2014-02-16
Why can't it boot into windows? Maybe the same issueis keeping it from booting linux? What happens when you power on without the usb drives?

---

### Post by phemt2 on 2014-02-17
> **bookrt said:**
> Why can't it boot into windows? Maybe the same  issueis keeping it from booting linux?

I'm not sure. It's either an HDD failure or something else I'm not aware of.

Would that keep it from booting up? Is there any hardware component that would keep a USB pendrive from booting up Ubuntu?

> **bookrt said:**
> What happens when you power on  without the usb drives?

> **phemt2 said:**
> No like I said, I can't get past the blinking cursor screen. If I stick a pendrive in one of the USB slots I get the blinking cursor on screen. **Without any USB drives attached I get "*Reboot and Select proper Boot device* or Insert Boot Media in selected Boot device and press a key"**.

---

### Post by sudodus on 2014-02-17
I suggest you check if the USB pendrives can boot another computer. If they do, and you still get that blinking cursor in this particular computer, I think it is a driver problem, maybe the graphics driver or wifi driver, maybe some other driver. Please try with several boot options (start with nomodeset) according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by fdrake on 2014-02-17
@phemt2
you said that booting from the usb you get only a blinking cursor. What happens after that? How long does the blinking cursor stays there?  does it hangs in there or it tries to boot windows?

what is the error message that you get while trying to boot into windows( xp?) ?

---

### Post by Plurtu on 2014-03-04
I had the same problem, it was just booting straight to a blank screen with blinking cursor.

System:
Asus EeePC 1001P BIOS 1202 (latest)

Images tried:
lubuntu-13.10-desktop-i386.iso   
lubuntu-13.10-alternate-i386.iso   
lubuntu-10.04-desktop-i386.iso 
 debian-live-7.4-i386-standard.iso

USB boot software tried:
Universal-USB-Installer (full format)
YUMI
UNetbootin

USB sticks tried:
4GB Imation
8GB Verbatim

The problem for me turned out to be the USB sticks. Changed to a SanDisk Cruzer Blade 8GB and it worked (using YUMI).

---

### Post by sudodus on 2014-03-04
Welcome to the Ubuntu Forums *Plurtu*, and thanks for sharing your experience with USB sticks :-)

I have also noticed that some computers (motherboards and USB systems) have problems with some USB sticks. See also these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)
[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

