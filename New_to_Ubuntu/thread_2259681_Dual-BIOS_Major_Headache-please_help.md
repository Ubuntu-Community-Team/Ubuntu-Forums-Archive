---
title: "Dual-BIOS Major Headache-please help"
date: 2015-01-06
forum: New to Ubuntu
---

### Post by Yosef_Karo on 2015-01-06
I am trying everything I can think of to get the computer to boot from USB to install Ubuntu on my harddrive.  After changing all boot priority to USB-HDD, and even hitting F12 for boot menu and selecting USB-HDD, no matter what, it would always go straight to Windows boot up.  Finally, I unplugged my internal HDD and it finally booted from my USB thumb drive.  I am 'live' right now.  But you can imagine what happens when I re-plugin my internal HDD... I guess it always happens, I'm no PC expert... but it is as if it is not there.  Maybe it has to be recognized by BIOS at boot?  I don't know, but I am unable to install Ubuntu to it.  It is as if it doesn't exist.

I really want to install Ubuntu and need help.  What can I do now while I am still live to get the HDD recognized so I can get rid of the Windows and install Ubuntu to it?

P.S. Dual BIOS sux.

---

### Post by grahammechanical on 2015-01-06
It would help us to help you if you gave us details of the computer hardware, the Windows version installed and the version of Ubuntu that you are trying to install.

On my machine, which is more than 7 years old and has the old BIOS boot system and not the newer UEFI boot system, it is not enough to change boot priority. I have to go to the boot section and select it as a removable hard drive. 

I cannot give more advice than that without more information on your computer set up. Do you see the problem?

Regards,

---

### Post by Yosef_Karo on 2015-01-06
Sorry, new to all of this:

Mother Board: Gigabyte GA-G41M-ES2L  no version so V.1
HDD:               Samsung HD502HJ

output from lspci:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
03:00.0 PCI bridge: Pericom Semiconductor PI7C8140A PCI-to-PCI Bridge
04:0c.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:0d.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:0e.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:0f.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)


Windows OS: Windows 8 Pro 64-bit

I tiried hard to find anything in BIOS about a booting from removable device and found nothing... Cannot for the life of me figure out how to boot from my USB as long as the internal HDD is plugged in.  I hope that you are someone else can help me to solve this thread.

---

### Post by Yosef_Karo on 2015-01-06
Just noticed says nothing about CPU.  It is a dual core, something like E2220, E2222, something like that.

---

### Post by Yosef_Karo on 2015-01-06
Oh, version of Ubuntu that I want to install is the latest LTS.

---

### Post by coldraven on 2015-01-06
Check that you do not have a memory card left in your card reader. I sometimes forget to remove one and it will prevent USB booting.
You could also choose a different USB port, I read somewhere that a USB 3 port would cause a problem.

---

### Post by buzzingrobot on 2015-01-06
Does your BIOS show any other drives besides the drive Windows is installed on and the "USB-HDD"?

---

### Post by Yosef_Karo on 2015-01-06
Unbelivable!  Something as simple as plugging in the boot up USB stick into a different USB port can make all of the difference in the world!  Thank you coldraven.  I now have Ubuntu 14.04 LTS completely installed on my HDD.  No more Windows!  Thanks in part to the installer no longer having the option to "install alongside Windows" no doubt. lol  Oh well, who needs 'em anyways.  I'm back!

---

### Post by Dennis N on 2015-01-06
Be sure you are booting from a powered off state, not restarting. Restart may not work on some systems to see the usb. Then try for the one-time boot menu by repeatedly pressing the appropriate key on startup.

---

### Post by Yosef_Karo on 2015-01-06
Thanks buzzingrobot for the assistance!  This thread is solved.

---

### Post by Yosef_Karo on 2015-01-06
Dennis N, that was also a factor, thank you!

---

