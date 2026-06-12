---
title: "RE: Ubuntu was official OS, need it back"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by jason182 on 2015-06-20
Hello all,

I did a very stupid thing, I brought a HP255 and when i got it back played around with ubuntu, and thought that windows is easier as its what i'm used to... Now i installed vista and it has errored all my drivers, I've tried re-installing ubuntu and system factory reset but no luck!!!, Really worrying now.... can anyone assist? just want ubuntu back  so when it loads the laptop it goes straight back to ubuntu :(

---

### Post by brian80 on 2015-06-20
Hi jason,

Don't panic as we can fix this fairly easily.
If you want to remove everything including vista (assuming they are on the same drive) you could fallow these instructions
First thing you should do is run ubuntu from a live disk or usb.
Next open open gparted and find your disk.
After that format your disk to ext4.
Reboot and try to reinstall ubuntu from the live disk.

Let us know if you encounter any more problems.

---

### Post by QIII on 2015-06-20
Just to be sure...

You want ONLY Ubuntu on the machine?  Do you also still want to be able to dual boot Windows when you want to?

---

### Post by jason182 on 2015-06-20
No it originally came with Ubuntu, i only want Ubuntu on there, whole things giving me a headache, I do apologize Brian im not 100% understanding what your saying, been trying to fix this since 4pm its no 12 >_<

---

### Post by QIII on 2015-06-20
The very first thing I would do is get some sleep.  :)  These things are just not worth this level of frustration.
  
The forum will still be here in the morning when your head is clear.

---

### Post by jason182 on 2015-06-20
Issue is, I need this for the morning, "Fathers day present" =/

---

### Post by QIII on 2015-06-20
OK.

Did it come with an Ubuntu installation DVD?

---

### Post by sudodus on 2015-06-20
You are happy to overwrite Windows, and so is Ubuntu too. Have you got an Ubuntu install DVD or USB drive? If not, download an Ubuntu desktop iso file, I would suggest Ubuntu 14.04.1 LTS (with long time support).

Check that the download was good with md5sum.

Make a boot DVD disk or USB pendrive with Ubuntu.

Boot the computer from the drive with Ubuntu.

Start the installer, and at the partitioning page, install Ubuntu to the whole drive.

Then Ubuntu will use the whole internal drive and use the main part for the root partition and a small part for the swap partition.

When the installation has finished, you can reboot the computer and remove the DVD disk or USB pendrive with Ubuntu. The computer should now boot into the installed Ubuntu system.

Please ask about details, if you need help with any of these steps. If I or someone else disappears from the keyboard and goes to bed, there will be other people in other time-zones, that can help you :-)

---

### Post by RobGoss on 2015-06-20
As always great advice here but just wanted to add my 2-cent here is the Ubuntu help section on installing Ubuntu pretty simple and straight forward. [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) Good luck

---

### Post by jason182 on 2015-06-21
I keep going around in circles here, The laptop doesn't want to boot by cd -.- im so annoyed with this!

---

### Post by sudodus on 2015-06-21
What CD is it? The Ubuntu iso files are bigger than what can be squeezed into a CD, so you need a DVD disk or a USB pendrive to boot from.

What do you see, when inserting the CD into another (and running) computer? One big iso file (wrong) - or several directories and files (correct)?

Did you burn 'image to disk' with a low burning speed as possible?

 Which version of Ubuntu is it?

What output is there (how far does the boot go)?

Is the computer in UEFI mode or BIOS mode?

How do you select to boot from the CD?

Have you put optical media (CD/DVD) before internal HDD in the boot order in the UEFI/BIOS menus?

An alternative is to boot from a USB pendrive - many people prefer that method nowadays.

See this link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by asgard2 on 2015-06-21
> **sudodus said:**
> 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I would use unetbootin for a bootable USB-Stick, also described in this link.


If you burned the ubuntu iso file correctly as an image to the DVD, it should boot. 
If not, you need to press a button directly after power on and enter the boot menu, it is maybe "ESC", or another F-Key, depending on your device.

---

### Post by stalkingwolf on 2015-06-21
either f8 or f10 on boot will bring up the boot menu . select the dvd drive and it should boot

---

### Post by Vladlenin5000 on 2015-06-21
> **stalkingwolf said:**
> either f8 or f10 on boot will bring up the boot menu . select the dvd drive and it should boot

Actually it's ESC (during post) then F9 (in UEFI menu) for one time boot options. You want to boot in UEFI mode as well*. The one time boot menu - or any other for that matter - won't recognized any non bootable device. Assuming you have a correctly burned DVD (not CD) or a properly made USB flash device and CSM (legacy) as an option** there will be 2 entries for each given bootable device, one starting with UEFI. 


* Ubuntu can be installed either way but for any newer machine, whenever possible, UEFI mode is recommended.
** You must have if you installed Vista (the absolutely WORSE Windows you could've picked up for a low end AMD APU based notebook - Windows 8.1 or newer, always, not even Seven works as it should in those machines).

---

### Post by monkeybrain20122 on 2015-06-22
Just disable uefi and use bios. There is no advantage of that but can potentially make life difficult

---

