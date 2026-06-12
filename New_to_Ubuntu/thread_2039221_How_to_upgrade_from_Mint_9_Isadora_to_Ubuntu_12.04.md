---
title: "How to upgrade from Mint 9 Isadora to Ubuntu 12.04"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by ruslan kim on 2012-08-08
Hey everyone, I'm just a Linux beginner, so I need some help. My situation is this. Few days ago I installed Linux Mint 9 Isadora and removed Windows 7 completely from my PC. Now there is only one OS. Now I would like to upgrade to Ubuntu 12.04 LTS (64 bit). How can I do it from Mint 9?

Please explain me as simple as possible =) Thanx in advance!

---

### Post by cortman on 2012-08-08
> **ruslan kim said:**
> Hey everyone, I'm just a Linux beginner, so I need some help. My situation is this. Few days ago I installed Linux Mint 9 Isadora and removed Windows 7 completely from my PC. Now there is only one OS. Now I would like to upgrade to Ubuntu 12.04 LTS (64 bit). How can I do it from Mint 9?

Please explain me as simple as possible =) Thanx in advance!

To upgrade from Mint to Ubuntu is not possible. Either do a fresh Ubuntu or Mint installation (it'll be cleaner and likely more stable anyway).

---

### Post by darkapec on 2012-08-08
Not possible, at least not easily possible. Linux mint is based off debian just like ubuntu but as far as I know upgrading from mint to ubuntu is not possible. You will have to go to ubuntu.com and download ubuntu 12.04 and burn the ISO to a disk and do a fresh install. 

If you need help with that process just post back and I can walk you through it (I assume you can handle it because you managed to install mint)

in addition upgrading from any 32bit os to 64bit os is also not possible at this time so make sure you get the 64bit version from the ubuntu website.

---

### Post by NikTh on 2012-08-08
Hi , 
I think you can't . Linux Mint is another OS . OK it is Ubuntu-based , but another distribution. 
From Linux mint 9 you can upgrade to a Linux Mint newer version , like Linux Mint 13 (I think this is the latest). 

If you want Ubuntu 12.04 , then download and burn the .iso and make a full Install. 
You can remove (replace) Linux mint or you can install Ubuntu 12.04 alongside Linux Mint (so you will have both Operating Systems). 
Good Luck 
Thanks

---

### Post by ruslan kim on 2012-08-08
I guess I'll just uninstall Mint and make a clean start with Ubuntu. But how to do it? The iso that I found on the official website seems to be for Windows only. I would be very grateful for step-by-step guidance =)

Plus I can erase everything on the HDD cause I have made a backup of all important information

---

### Post by darkapec on 2012-08-08
Download 64bit 12.04 from here

[http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=lts](http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=lts)

once completed just open with the included Mint burning utility I know ubuntus is Brasero, not sure if Mint has included the same one or not. 

Once the disk is burned restart your computer and boot from the CD and the GUI will guide you the rest of the way. 

Let us know if you need more help.

---

### Post by audiomick on 2012-08-08
You sound like someone who may want to try different OS over the course of time. You might want to think about putting your /home directory on a seperate partition. That way, you can re-mount it to a new install, either as /home or as a data partition, thereby avoiding having to copy off your data, and then back on after a new install. To do this, choose the manual option when you get to the partitioning bit of the installation process. That is where it offers you options like "install beside windows" or "use the whole drive". I think the option for manual partitioning is called "something else" these days on the Ubuntu installer.

---

### Post by NikTh on 2012-08-08
> **ruslan kim said:**
> I guess I'll just uninstall Mint and make a clean start with Ubuntu. But how to do it? The iso that I found on the official website seems to be for Windows only. I would be very grateful for step-by-step guidance =)

Plus I can erase everything on the HDD cause I have made a backup of all important information


Hi , 
except of what @darkapec suggested (with CD) you can also burn the .iso on Usb. 
Try Unetbootin --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Install unetbootin in Linux Mint 9 and burn the .iso of Ubuntu 12.04 to an empty Usb stick (at least 2GBs) 
Then boot from Usb and click on "Default" , when Desktop Environment opens , you can take a tour to check if Ubuntu works well with your hardware and after that click on "Install Ubuntu" (you will have an Icon on Desktop with that prompt). 
Once you click "Install Ubuntu" Ubuntu's installer will open . Fill up all necessary information and once the options of install pop up , select "Install Ubuntu to whole disk" it will have a warning like "This will erase everything from Disk" . This option will clear up your Linux Mint installation (everything) and will install Ubuntu to whole disk. 
Ubuntu's installer will take care of all work to be done , automatically. 
Thanks

---

### Post by ruslan kim on 2012-08-08
> **darkapec said:**
> Download 64bit 12.04 from here

[http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=lts](http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=lts)

once completed just open with the included Mint burning utility I know ubuntus is Brasero, not sure if Mint has included the same one or not. 

Once the disk is burned restart your computer and boot from the CD and the GUI will guide you the rest of the way. 

Let us know if you need more help.


Thank you.
I already have the iso, I have burned it on Windows couple days ago. I tried restarting with the CD and this is what I have now. I could choose between booting from HDD or from CD. I tried both variants but both of them result in launching Linux Mint. I expected booting from CD to launch Ubuntu setup, but no)))

What can it be? A BIOS issue or smth else? I am on HP Pavillion laptop. Thank you for the help.

I'll try booting from USB now...

---

### Post by darkapec on 2012-08-08
Its hard to say why the system did not boot from cd. 

First thing I would check is boot up into your computers BIOS and change the BOOT order to 1. CD DRIVE / DVD DRIVE 2. HARD DRIVE
(I have noticed on some systems simply selecting the BOOT MENU VIA F12 does NOT boot from the cd correctly, so it must be set to boot from the CD drive within the BIOS)

I have also had this problem when I burned a ubuntu cd to a DVD. So if you burned the iso to a DVD that could be the issue. 

If you are still unable to get this method to work... The unetbootin might be another option, as long as you have a flash drive. unetbootin is an automatic USB installer. If your computer supports booting from a USB drive it will allow you to install ubuntu to a flash drive and install it that way. I would only use this as a last resort simply because you already have the CD burned and its the same process to boot from a USB drive as it is a CD.  I would only recommend unetbootin if your using a netbook or a computer with a broken cd drive. 

Hopefully you are able to boot from the cd this time

---

### Post by audiomick on 2012-08-08
> **ruslan kim said:**
> I expected booting from CD to launch Ubuntu setup, but no)))

Assuming that the CD is ok, when you chose to boot to the CD, you should actually get a page where you can either install Ubuntu or "try without installing" which is booting into Ubuntu in the live environment.

Going by your description, I would not discount the possibility that the CD is just no bootable for whatever reason. Can you try it on another machine, or conversely boot your machine to a known good CD? If you tell the machine to boot to CD and it doesn't find anything bootable there, it will go through it's options until it find something it can boot. like the mint install.

---

### Post by ruslan kim on 2012-08-08
All right! Booting from the USB stick worked! The problem is solved, I want to thank everybody so much for your help! \\:D/

---

### Post by NikTh on 2012-08-08
> **ruslan kim said:**
> All right! Booting from the USB stick worked! The problem is solved, I want to thank everybody so much for your help! \\:D/

Glad it worked . 

Please mark the **thread as solved **, by clicking on **Thread Tools**.
Thanks

---

