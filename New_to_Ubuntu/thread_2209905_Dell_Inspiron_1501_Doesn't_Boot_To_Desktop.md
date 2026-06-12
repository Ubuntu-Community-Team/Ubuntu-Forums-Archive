---
title: "Dell Inspiron 1501 Doesn't Boot To Desktop"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by greengeek2 on 2014-03-07
Hello.

I just installed Lubuntu 13.10 and removed Vista Basics. The bios* was changed for the hardrive to start first. 

However, when I press the power button, I never know how I will get to Lubuntu Desktop. I ALWAYS get:

Warning: The battery** cannot be identified. The system will be unable to change this battery.
Press any key to continue.
Press <F2> 2 times to enter setup
Press <F12> and any key to enter boot menu.

I press the space bar. After that:

Version 1:
Sometimes it goes to desktop.

Version 2:
Sometimes it goes to grey screen with different colors of vertical lines.

Version 3:
Sometimes it goes to grub. From grub, I have to down arrow and click the recovery mode. OR sometimes I have to click a few more times in grub to get to "Normal Boot" and THEN it goes to desktop.

* bios v2.4.1 (need to upgrade to v2.6.3 A16. Don't know how yet or if I HAVE to; have researched but most queries are old)
** the battery is totally dead, does not recharge

Any help would be appreciated.

---

### Post by phidia on 2014-03-07
There is a chance that [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") can help you. If it does it is the easy way to get your system working. If not then report back and we'll try something else.

---

### Post by Vladlenin5000 on 2014-03-07
Indeed you need to update the BIOS for the latest (and last) version in order to avoid the error. Version v.2.6.3, A16 has the following changelog:
```
=============================================================================== 1. Fixed erroneous Bad Battery message during post. ===============================================================================
```

---

### Post by mörgæs on 2014-03-08
Agree that a new BIOS is worth trying.
It would have been easier to upgrade it under Windows, but you might be able to do it using a USB stick with Freedos.

---

### Post by greengeek2 on 2014-03-08
> **phidia said:**
> There is a chance that [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") can help you. If it does it is the easy way to get your system working. If not then report back and we'll try something else.

Thanks for the "boot-repair" advice. I tried it and looked at the results at paste-bin. The only thing I could understand was at the way bottom which said:

563 Boot successfully repaired.  
565 You can now reboot your computer.

However, when I started the laptop, I got the same old responses.

---

### Post by greengeek2 on 2014-03-08
> **mörgæs said:**
> Agree that a new BIOS is worth trying.
It would have been easier to upgrade it under Windows, but you might be able to do it using a USB stick with Freedos.

Thank you for your input. I looked at: [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS) and saw the different options. I'm looking for the instructions that WON'T turn the laptop into a brick (the owner might get a tad angry). :D

Can you provide a link to easy instructions that are idiot proof? :lolflag:

fyi: How I found which driver I needed: [http://www.dell.com/support/my-support/us/en/19](http://www.dell.com/support/my-support/us/en/19)

---

### Post by mörgæs on 2014-03-08
I thought I already did: A USB stick with Freedos.

I wouldn't be afraid to update the BIOS on a Dell. Other brands like Fujitsu Siemens are more risky.

---

### Post by Buenadriver on 2014-03-08
How did you install Ubuntu in the first place? From a cd or usb drive?

---

### Post by greengeek2 on 2014-03-08
> **mörgæs said:**
> I thought I already did: A USB stick with Freedos.

I wouldn't be afraid to update the BIOS on a Dell. Other brands like Fujitsu Siemens are more risky.

No, you provided no link to easy instructions, just suggested I use a USB stick and Freedos. I'm still looking for instructions that are easy enough for me to understand. 

I found this link: [http://java2go.blogspot.co.uk/2010/05/how-to-upgrade-your-dells-bios-directly.html](http://java2go.blogspot.co.uk/2010/05/how-to-upgrade-your-dells-bios-directly.html) from this website: [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS). I don't know if this will work since this "how-to" is from 2010.

Thanks for your insight on Fujitsu Siemens, glad I don't have one!

---

### Post by Buenadriver on 2014-03-08
I have a 1501 also, and I went thru that screen with vertical lines. What I did was put my install cd in the drive, and boot up. When the F2 F12 option came up I clicked on F12 and booted from the CD. It asked if I wanted to install and I went ahead with the install. When the FIRST QUIT button appeared. I clicked on that, and the 2nd QUIT button. Then it went ahead and booted to the desktop. On the desktop was an icon that said install Ubuntu. I clicked on that and did a complete install. Worked ok ever since. I hope that solves your problem, others may have a better way. Cheers.

---

### Post by greengeek2 on 2014-03-11
Hello Buenadriver, I installed Lubuntu with an USB drive.

---

### Post by greengeek2 on 2014-03-11
Thanks for sharing your experience. What bios version do you have installed? I have bios v2.4.1

In terminal: sudo getSystemId

---

### Post by greengeek2 on 2014-03-12
re: Trying to upgrade bios, do not have microsoft installed only lubuntu

No luck so far.

I tried: "What worked for one user on a Dell Inspiron 1525 and Xubuntu, using Wine to extract BIOS image etc" ([https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS))

I got stuck on line: wine 1525_A17.EXE  -writehdrfile -nopause

I got this response: mfc42

I tried to install with winetricks with no luck.

Then I found and tried: "Using UNetbootin to create a Linux USB from Linux", option 2. ([http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)) and installed freedos.

After I rebooted, I got this response: boot invalid or corrupt kernel image

Looked for a mirror download for freedos iso with no luck.

Yes, I did change boot order so that the USB is first. 

Any ideas?

Thanks in advance.

---

