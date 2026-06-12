---
title: "No WIFI with Dell 1350 Wireless card"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2011-10-25
I want to install Lubuntu 11.10 on an old Dell Inspiron 1000 with an external Dell wireless 1350 card.  It currently has Ubuntu 10.04 installed and the card works well, but I had to get the driver from the Internet with a wired (ether net) connection because alas Dell used cheap Broadcom cards back in the day.  They may still do.  The problem is that we travel and rely exclusively on WIFI for connection to the Internet.  The current OS was installed at a location where we had access to a wired Internet access so there was not a problem.  The question is, can I retrieve the required stuff from somewhere with another computer, transfer it to a flash drive, and then install in to the Dell.  What are the procedures or is it as simple as finding it, downloading it to a flash drive, and mounting the flash drive on the Dell so the information can be extracted there and installed to make the WIFI work.

---

### Post by garvinrick4 on 2011-10-25
That is the b43 drivers I do believe. Yes no problems with that driver and think it is 
bcm4306/3
it needs:
firmware-b43-installer
b43-fwcutter

Boot up with wired and open Synaptic and type b43 in search window and install these two.
Type bcm in search window and make sure nothing else installed at all in bcm group and take wire out and reboot.

Or can
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

---

### Post by Rex Bouwense on 2011-10-25
Thanks for the quick reply.  I don't think I made myself clear.  I have no wired connection.  However, I have another computer, an ASUS, with which I can download.  It is connected to the Internet via WIFI.  The Dell will not connect because it has the stupid card with the Broadcom chip set.  What I want to do if possible is download the firmware/driver to a flash drive with the ASUS and then transfer the downloaded information to the Dell which will then have all the goodies that it needs to connect to the Internet.  Is that possible?

---

### Post by garvinrick4 on 2011-10-25
Yes you can download to flash and then bring over to Operating System and install.
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by garvinrick4 on 2011-10-25
I downloaded debian for both and installed by:
 Dragging and dropping from Flash to drive to Operating system desktop:
```
cd Desktop
```
```
sudo dpkg -i *.deb
```Both installed fine and are nice and easy to install. One is either 32 or 64 bit.

[http://packages.debian.org/squeeze/b43-fwcutter](http://packages.debian.org/squeeze/b43-fwcutter)
[http://packages.debian.org/squeeze/all/firmware-b43-installer/download](http://packages.debian.org/squeeze/all/firmware-b43-installer/download)

---

