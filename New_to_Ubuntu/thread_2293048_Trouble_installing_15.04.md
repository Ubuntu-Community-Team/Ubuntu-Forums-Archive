---
title: "Trouble installing 15.04"
date: 2015-09-02
forum: New to Ubuntu
---

### Post by izuchukwu on 2015-09-02
i recently tried installing an ubuntu 15.04 using a usb but it booted to a command line interface. please what should i do?

---

### Post by howefield on 2015-09-02
> **izuchukwu said:**
> i recently tried installing an ubuntu 15.04 using a usb but it booted to a command line interface. please what should i do?

Learn some terminal commands ?

Some more information would be good, like your machine specifications and the name of the iso that you downloaded, for starters.

---

### Post by izuchukwu on 2015-09-02
i want to install it alongside a windows 10, am using hp 250 g1, the Iso is ubuntu-15.04-desktop-amd64

---

### Post by The Cog on 2015-09-02
Is it the USB stick that booted to a text prompt, or was it the installed Ubuntu?
What was the prompt?
Were there any error messages?

---

### Post by izuchukwu on 2015-09-02
it was the usb not the installed ubuntu

---

### Post by gamblitis on 2015-09-02
Maybe a silly question and not to undermine your intelligence but did you download the desktop iso or the server software?
I made that mistake at the very start.

---

### Post by izuchukwu on 2015-09-02
i downloaded the desktop iso not the server software, i cross checked now, it's the desktop iso i downloaded

---

### Post by gamblitis on 2015-09-02
Right well give us a run down of the steps you took.
Any errors you get.

Personally I would just suggest wiping the usb, and repeating the installation again.

---

### Post by yancek on 2015-09-02
How did you get the Ubuntu iso on the flash drive, what software did you use to make it bootable?
Is windows 10 installed using UEFI to boot or the older MBR method?

---

### Post by Bucky Ball on 2015-09-02
Changed thread title to increase your chances of support. Most people here need help. Good luck. :)

---

### Post by grahammechanical on 2015-09-02
We are not clear at what point the loading process failed. That is why we are asking these questions. Usually we see a purple screen with an icon of a human and an icon of a keyboard. If you see that screen press Enter. You will then be asked to select a language. The default is English. Select the lanuguage of your choice and press Enter, The underlaying screen should give us the options to Try Ubuntu; Install Ubunutu and some other options. Press F6

This wiki page will show you what you are looking for and what you can try. Go down to the section called Change the CD's Default Boot Options. Look for section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You may need to add the nomodeset option. We do that by selecting it from the menu that appears. To get back to the Try - Install page press ESC. You may need to try a combination of the F6 options to get the live session loading on your machine.

Regards.

---

### Post by ethan27 on 2015-09-03
Here is a solution that may work. I used this application to install Ubuntu 14.04. 1: Download Universal USB Installer: [www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") 2: Choose Ubuntu and your ISO you have already downloaded. 3: Select the CORRECT drive otherwise you may accidentally format your current SSD/HDD. 4: Wait for the process to complete. 5: Reboot into BIOS select to boot from USB. 6: Save changes and exit and install Ubuntu. Any Questions? Just post a reply and if I can I will answer your question.

Good Luck,
Ethan

---

### Post by Geoffrey_Arndt on 2015-09-04
Izuchuk . . . the chance of getting any real help are near zero *based on the zero info you have shared regarding your hardware* (PC).

What make?

What model?

What graphics?  (like nvidia, ati/amd/intel).   (not likely to be Intel graphics, as 99.5% of those machines install Ubuntu with no problems).

What cpu (dual, quad, speed)?

What ram?  (512, 1 gb, 2 gb, 4 gb, 64 gb, etc.)

What is size of HDD (hard disk drive)?

Does it already have free space for Ubuntu, or is it still all Windows OS and file system (ntfs)?

If you have created a partition for Ubuntu - what file system if any did you select?

Is it a PC newer than about mid-2010 (most of which use the newer "UEFI" instead of traditional "BIOS" for firmware . . . this is important, important, important)

And last but not least, are you wanting a dual-boot, or running Ubuntu only?

EDIT:   I see you are wanting to install alongside Windows 10, but it make take "the old college try".

Note also, you can have a dual-boot Win 10 and Ubuntu system without doing the install yourself, , , there are small computer integrators that can do that for you.    Setup takes maybe 5 minutes:    

See list here:     [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

