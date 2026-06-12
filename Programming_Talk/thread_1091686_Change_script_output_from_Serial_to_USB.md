---
title: "Change script output from Serial to USB?"
date: 2009-03-09
forum: Programming Talk
---

### Post by brucewestfall on 2009-03-09
I have read the stickies and did a search for USB, but cannot find what I'm looking for yet.

I have a script that drives a vinyl cutter from Inkscape.  I have a new computer that has no serial port...

The original line from the script is:
CUTTER=/dev/ttyS0
stty 9600 cs8 -parenb -parodd crtscts -ixon -ixoff -F /dev/ttyS0

How do I change it so it will output to a USB device?

Running lshal and dmesg led me to learn my plotter is hooked up to:
/dev/bus/usb/004/002

Any ideas?  I don't need to cut something immediately, but I'm getting worried...

---

### Post by geraldm on 2009-03-09
Try these two commands:
lsusb
find /sys/devices/pci0000:00 -name "tty*" -print

the last command on another computer returns thus:
/sys/devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.0/ttyUSB0
/sys/devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.0/ttyUSB0/tty
/sys/devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.0/ttyUSB0/ttyUSB0

If you get an output like the above, you might only need to change the device 
name from ttyS0 to /dev/ttyUSB0 (if you get lucky.  This is untested, and 
whether it works may depend on how well the USB device serial driver is integrated with a tty device.)  Post what driver is being used, if you find out.

regards,
Gerald

---

### Post by brucewestfall on 2009-03-10
Here are the outputs:
bruce@Brutus:~$ lsusb
Bus 006 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 005: ID 04f9:01b1 Brother Industries, Ltd MFC-665CW Remote Setup Port
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bruce@Brutus:~$ find /sys/devices/pci0000:00 -name "tty*" -print


I found out that the plotter is on Bus 004 (via dmesg), and the last command returns nothing.

Thanks for the idea.  I sure wish it would've worked, but do you have a Plan B?

You just saw my Plan B....

---

### Post by supirman on 2009-03-10
You can get a usb-serial adapter ([http://www.vpi.us/usb-serial.html](http://www.vpi.us/usb-serial.html)).  It should then show up as /dev/ttyUSB0 similar and you can simply use that as your serial port.

---

### Post by cszikszoy on 2009-03-10
USB to serial adapters work well.  If you decide to go this route be careful and get a cable with a good usb->serial driver chip.  In my experience, cables based on the FTDI chip worked very well (completely plug and play) with linux.  I had a cable based on the prolific chip that didn't work at all.

There are cheap ones on ebay: [http://shop.ebay.com/?_from=R40&_trksid=m38.l1313&_nkw=ftdi+usb+serial&_sacat=See-All-Categories](http://shop.ebay.com/?_from=R40&_trksid=m38.l1313&_nkw=ftdi+usb+serial&_sacat=See-All-Categories)

---

### Post by geraldm on 2009-03-11
brucewestfall:
You may be testing on an older OS.  I was using a liveCD running  Ibex, which
 uses the sysfs filesystem.  If your OS does not have this filesystem
your plan B may also involve a newer OS.  You can check for the filesystem 
by executing 
cat /proc/filesystems | grep sysfs -
 It should provide a line saying "nodev  sysfs" or equivalent if it is present.

I am using devices with the prolific chip, manufactured by two different companies.  I can get them to communicate, but have not yet found out how to
set the speed to be used.  I was expecting to use the sysfs filesystem to make 
any needed tweaks.  Has anyone seen any tutorial or HOWTO  using the prolific 
chip?

regards,
Gerald

---

