---
title: "Huawei E220 USB modem"
date: 2006-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by nickwallingford on 2006-11-18
The Huawei E220 is a USB 'dongle' for HSDPA connection through (for me, anyway) the Vodaphone network in New Zealand.

When inserted into a Ubuntu OS (Edgy in my case), it is immediately detected as a SCSI/CDROM type bulk storage device, and the files that are used by Windows appear attached to the filesystem similar to any other USB storage device.

Close any window that might be showing you those files. Then unmount the device (eject the CDROM icon you'll find on the desktop created when you inserted the device).

All commands I give here are just the commands - you will likely need to put 'sudo' in front of them so you have the permissions of root to carry them out...

Insert the device and give it a chance to settle down (enjoy watching the lights flash...)

When you insert the device and it gets recognised as a storage device, it will have created /dev/ttyUSB0. You can see that with:

**ls -la /dev/ttyU***

You will likely only see one entry: ttyUSB0.

To make the modem work, you must first remove the module that is used for usb-storage devices. First, let's see that it is inserted for you:

**lsmod|grep usb_storage**

You should see it referenced several times, similar to my output:

[B]usb_storage            75072  0 
libusual               17040  1 usb_storage
usbcore               134912  7 usb_storage,usbserial,libusual,usbhid,ehci_hcd,uhci_hcd
scsi_mod              144648  5 sd_mod,usb_storage,sg,sr_mod,libata[/B]

Now we'll remove that module:

**rmmod usb-storage**

If you are told it is in use, that is an indication you didn't close windows and eject the device first.

You can re-issue the lsmod command to confirm it is gone...

This next command may not be absolutely necessary, but it won't hurt anything (heh, heh...):

**rmmod usb-serial**

You are now going to re-insert that module, but giving the specific details of your modem. First, make sure you have the right details by using:

**lsusb**

You should see an entry similar to this in the output:

**Bus 004 Device 004: ID 12d1:1003**

The Bus and/or Device number might be different for you, but the important part is the ID. If yours is not 12d1:1003, you'll need to modify the next command, but I *think* it will be either that or 12d1:1001...

This command will insert the module with the device specific details:

[B]
modprobe usbserial vendor=0x12d1 product=0x1003[/B]

Now, remove the device, wait a bit for things to settle, and then plug it back in.

I *think* you may now have maybe three entries if you do:

**ls -la /dev/ttyU***

Basically, what has been done is that you have removed the initial inclination to treat the device only as a bulk storage (removing the module that handles that). You've also manually caused the recognition of the device (using the modprobe command). So that when you re-plugged it, it should now be able to work with the *modem* part of the device addressing it as /dev/ttyUSB0, rather than that being the bulk storage device.

Use a text editor such as pico to edit or create if necessary the file to handle the dialling configuration. My /etc/wvdial.conf file looks like this:

[B]# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem[/B]


I've only put in the relevant sections - the full file can be found at the address below in this posting.

You can dial the modem with:

**wvdial hsdpa**

If all is happy, you'll see the messages in the terminal window to show how it is connecting, your IP address, your remote gateway and 2 nameservers the network provides for you.

I do, sometimes, have to repeat the process or reissue some of the commands after re-inserting the device, but eventually it comes right - it hasn't been enough of a bother for me to get the process down *exactly* right...

Do remember the various need for 'sudo' unless you change ownerships/permissions. In particular, if it looks like you've connected but are not able to connect to any sites, etc, look for a message telling you that /etc/ppp/pap-secrets and /etc/ppp/chap-secrets are not able to be written to - that may well indicate that you for sure need to run the wvdial command as sudo (If you are running it as a normal user, that user would need to have the ability to write to those files for the connection to be able to work...)

I am writing this while standing on the shoulders of the knowledgeable and the helpful. In particular, see [http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726) - Post 1 in that thread, and Tazz_Tux who wrote and maintains it, has been invaluable. Go there if for no other reason than to get the latest version of wvdial.conf

Enjoy your Huawei E220 under Ubuntu!

Nick

---

### Post by Olangu on 2007-06-26
You can also use gnome-ppp for dialing.

For swedish HSDPA-provider tre (3) you want the following configuration.
First of all make sure you have disabled PIN-code check.

Then:

User: any
Pass: any

Telephone number: *99***1#

Modem:
Device: /dev/ttyUSB0
Type: Analog Modem
Speed: 460800

Init strings:
Init 2 : ATZ
Init 3 : ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init 5 : AT+CGDCONT=1,"IP","data.tre.se"

Under options you need to check "Ignore terminal strings (stupid mode)"

Now just dial.

Happy surfin!

---

### Post by mormor on 2008-03-04
or you can get vodafones driver here:

[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19)

vodafones drivers works fine in norway

---

### Post by jtreg on 2010-11-30
I am using Lucid Lynx and I am having problems with my model E1752Cu Huawei modem on O2 network. I paid for preloaded Pay and Go ... and I have read up on the suggestions to get it working...It still will not work. I am getting a single blue flash every 3 secs on it.

Do I need to download any driver for it? If so where from?

---

### Post by mahela007 on 2011-02-05
I know that it's quite possible that everyone has lost interest in this thread... but jtreg.. did you have any success with your modem?

---

### Post by DirkL on 2011-05-27
I have blacklisted usb_storage as follows: in /etc/modprobe.d/blacklist.conf, put the lines

# see discussion "Huawei E220, still having trouble" on [www.draisberghof.de]("http://www.draisberghof.de")
# Disconnect modem and manually `modprobe usb_storage` when needing a device.
# `rmmod usb_storage` afterwards
blacklist usb_storage

It's a bother, but I use my modem all the time and my USB disks only some of the time.

---

