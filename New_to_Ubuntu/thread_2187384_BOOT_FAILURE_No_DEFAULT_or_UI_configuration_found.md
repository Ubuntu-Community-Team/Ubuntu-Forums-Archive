---
title: "BOOT FAILURE: No DEFAULT or UI configuration found"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by linux.smurf on 2013-11-11
I got this computer which is a Dell Inspirion Mini single core 130GB HD from a friend awhile back, and well i wanted to install Ubuntu on it so I downloaded the 700MB ISO file to USB (since i dont have a cd/dvd rom), and i hit F12 to boot from the USB then I get the error.... i believe it was messed with before i got it, so i am wanting to wipe everything off and just run linux ubuntu, but im not all sure on how to do it, i used to have it on an Acer a year or so ago, but How do I fix the issues i am having and install the wonder that is Ubuntu from USB?

Windows Vistaq Home Basic Intel Atom CPU N270 @1.60GHZ 1,00 GB RAM
mobile Intel 945 Express Chipset Family

---

### Post by fantab on 2013-11-11
First of all do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded ubuntu.iso to confirm its integrity.  If the test fails to match then re-download the .iso.

Then re-BURN the .iso to the USB as suggested in the following links:
To burn from Windows: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
To burn from Ubuntu: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
OR use [UNETBOOTIN]("http://unetbootin.sourceforge.net/").

Check in the BIOS menu to see if USB bootin is enabled.
If all is good and if you reach the Ubuntu menu then "Try ubuntu without installing', and see how it fares on your machine.

EDIT: [Xubuntu]("http://xubuntu.org/about/") will be better suited for your machine and will perform faster than Ubuntu. Xubuntu is Ubuntu with [XFCE destop environment]("http://xfce.org/").

---

