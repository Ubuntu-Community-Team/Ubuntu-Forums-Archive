---
title: "Unable to Mount USB Drive"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Cashatoo on 2008-11-27
I just installed Ubuntu Eee (8.04) on my EeePC (I'd ask there for help but I'd like to ask here first due to more active users).  I tried inserting a USB flash drive and get the error "unable to mount" and the reason is that I need to be a super user in order to do so.  In trying to fix it I went into Users and Groups and made sure I had the privileges to access USB drives (which I did).  I looked up several things about superuser and ways to get this to work, but I'd like a way as a regular user just to put my flash drive in and be able to use it quickly.

---

### Post by Cashatoo on 2008-11-27
Also has anyone had problems connecting to a Linksys WRT54GL?

---

### Post by Olivier2371 on 2008-11-27
Hi there,

Do you use windows?

If so instead of removing the usb flash drive by unplugging it, try the function Safely Remove Hardware, and then unplug it.

To find out about your usb,
open terminal
then type

lsusb

---for your second post,---

what do you mean by problem connecting?

To determine what wireless card/chipset you have, open up a terminal and type the following.

lspci -v | less



To check the status on your wireless connection, use:

iwconfig

post both result here.

---

### Post by Cashatoo on 2008-11-27
Thanks for replying.

I tried inserting the flash drive into my Windows box and tried to safely remove and try again, but  still get an error (only superusers can use mount).

Result from lsusb:

Bus 005 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

That&#347; with nothing plugged in.

With the USB flash drive in:

Bus 005 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive

which is odd as it is only a 1 GB disk.

The wireless issue more clearly:  My Eee sees the network but when I try and connect nothing happens.

from lspci (there were more but I think these are the only relevant ones)

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8324
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

from iwconfig:

lo        no wireless extensions.

eth2      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-29 dBm  Noise level=-96 dBm
          Rx invalid nwid:2934  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Olivier2371 on 2008-11-27
What type of encryption are you using? (WPA/TKIP...WEP....NONE)

For your wireless I found this link.

[http://ubuntuforums.org/showthread.php?t=902860]("http://ubuntuforums.org/showthread.php?t=902860")

Check that the driver is enable first.
System->Administration->Hardware drivers


Give me a minute for your USB flash drive.

---

### Post by Cashatoo on 2008-11-28
I have no drivers listed when I look in Hardware Drivers.  I set my router to factory default to see if that helped and tried with no security, still no dice.  I was able to connect to a different router without a problem though.

---

### Post by Cashatoo on 2008-11-28
Got my wireless working.  I got ndiswrapper to work and installed a Windows driver and it worked like a charm.  I didn do this before because it wouldn work on straight Ubuntu just last week.  I still like to know if anyone has any input on the flash drive thing though.

---

### Post by Miks on 2008-11-28
> **Cashatoo said:**
> Got my wireless working.  I got ndiswrapper to work and installed a Windows driver and it worked like a charm.  I didn do this before because it wouldn work on straight Ubuntu just last week.  I still like to know if anyone has any input on the flash drive thing though.

Well done with ndiswrapper, sometimes the drivers can be a right <censored> :-)

Regarding your flash drive, it was most likely supposed to be 4GB when made but defects found in it forced the company to remove/butcher parts so that only the reliable bit - in this case 1GB is available.
Automount and udev should work their magic to present the USB drive but it's obviously having an off day.  Try this with it plugged in:

sudo fdisk -l
(this will show all the partitions - your 1GB drive should show up and tell you what it is.  Probably /dev/sdf1)

sudo mkdir /meda/usb
(First we make somewhere to mount)

sudo mount /dev/sdf1 /media/usb
(then we mount it and tell it where. Obviously if your stick isn't sdf1 change it appropriately)

sudo umount /media/usb
(This is how you unmount it before removing.)

---

### Post by anewguy on 2008-11-28
If may be neccessary to add permission in the /etc/udev/rules.d in order to mount this and access it as a normal user.

Please report back if none of the above worked for you and we'll work from there.

Dave :)

---

### Post by Cashatoo on 2008-11-28
> **Miks said:**
>  sudo mount /dev/sdf1 /media/usb
(then we mount it and tell it where. Obviously if your stick isn't sdf1 change it appropriately)

When I do this with sdf1 changed to sdb (from fdisk) I get:

mount: you must specify the filesystem type

anewguy:

could you be more specific as there are a lot of files in the rules.d folder and I couldn figure out which one did which.

Thanks.

---

### Post by anewguy on 2008-11-29
I'm just on my way out right now, but I'll be back later tonight and post the instructions for you!

Dave :)

EDIT:  Just back in.  Ithink this is what you should try:

open a terminal windows

su <enter>  -> use your regular password when prompted

cd /etc/udev/rules.d <enter>

gedit 45-my-flash.rules  <enter>  the file will be empty

add the following line:

SUBSYSTEM=="usb", ENV{devtype}=="usb_device", ATTRS{idVendor}=="0781", ATTRS{idProduct}=="5406", MODE:="0666"

save the file

exit

reboot

try your usb flash drive again - it should be accessable to everyone.

If that doesn't work let me know as there is also another place it may need to change to mount the usbfs as accessable by other than root.


let me know what happens.

Dave

---

### Post by Cashatoo on 2008-12-25
Many weeks after that post I am finally replying.  It didn't work, still get the same error about mounting the flash drive.

---

### Post by Dex73 on 2009-05-09
If you used the drive on a windows system and didn't remove it safely Linux will see it as logged on to another system and not mount it.

---

### Post by triffle on 2009-07-06
> **Cashatoo said:**
> Many weeks after that post I am finally replying.  It didn't work, still get the same error about mounting the flash drive.


Hey Everyone... I was having this same problem. Mine started when I created a "usb startup disk" so after alot of forum searching a googling... i finally found a fix that worked for me.... Here is the link... [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) please see after installing for the fix.

I guess what happens is that while booting from a usb flash drive you trick ubuntu into thinking that it is the CD Rom. You have to go into and edit your /etc/fstab from terminal

sudo gedit /etc/fstab

you will see a line towards the bottom of the page 

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

just put a comment in front of the line like this

#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

save and close

try and put your thumbstick back in and for me anyways tahh dahhh... Word!!!

Much Thanks to the ubuntu community...

---

### Post by daygan on 2010-05-26
I was having this problem but there was no line in the fstab file referencing my cd drive, so just in case anyone else has the same issue and comes along this thread, here's the solution:

regenerate your cd-specific /etc/udev/rules.d file (I came to this conclusion based on anewguy's post & the understanding that installing ubuntu from a usb may confuse your system and cause it to treat the usb as a cd)

1.Delete the file. For me, the file was 70-persistent-cd.rules (in the directory /etc/udev/rules.d) . I deleted it. (with super user permissions, of course)

2.Reinstall the udev package(as this thread: [http://forums.fedoraforum.org/showthread.php?t=201551](http://forums.fedoraforum.org/showthread.php?t=201551) told me that this would recreate the file automatically. Reinstalling before deleting the file didn't do the trick, so that's why I deleted the file.)

3. reboot, and usb mount permissions should be available. There may be a way to cause this to happen without a reboot, but I don't have enough Linux experience to know.

---

