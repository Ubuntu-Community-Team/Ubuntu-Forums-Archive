---
title: "HOWTO: Fix freezing on Thinkpads when swapping optical drives for batteries"
date: 2006-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by kaens on 2006-08-16
This isn't too hard to fix, but it's an annoying problem. When swapping an optical drive for a battery, Thinkpads (at the very least the T30 series) will freeze. 

This is due to the "eject" command not being sent to ibm_acpi when the release lever is pulled.

To fix this, you need to compile and install the module lt_hotswap, which can be found [here](http://sourceforge.net/projects/lths/).

Download the latest version of the module, read through the README.

To compile, make sure you have the source and headers (and build-essential) installed on your system. To install these, you can do this :

First, find the version of the kernel you are running:
```

cat /proc/version

```

This will give you output something like this:
> Linux version 2.6.x.x stuff.....
All you need to remember are the numbers

Now, you need to install the headers and sources for your kernel:
```

apt-cache search linux-source | grep those-numbers
apt-cache search linux-headers | grep those-numbers

```

now run 
```

sudo apt-get install names-of-packages-returned-by-apt-cache

```

Now change to the directory where you downloaded the lt_hotswap module and do the following:
```

tar xzf lt_hotswap-X.X.X
cd lt_hotswap-X.X.X
make
sudo make install

```

If everything went fine, we should be in business. To see what this adds, do this:

```

cat /proc/acpi/ibm/bay
#release the eject lever
cat /proc/acpi/ibm/bay
#should still be the same - push the lever back in
sudo modprobe lt_hotswap autoeject=1
cat /proc/acpi/ibm/bay
#release the eject lever
cat /proc/acpi/ibm/bay
#sweet.

```

Alright! You should be seeing the ststus go from occupied to unoccupied once you have issued the modprobe command.

Now you probably want this to load on boot. I know that I don't want to have to issue a modprobe command every time I startup my laptop. Normally, this would be a matter of adding a line to /etc/modules, and the options for the module in /etc/module.d/options. lt_hotswap, however, needs to be loaded after all the ACPI modules (so you probably could do this if you have all that compiled into your kernel) and for reasons unkown to me, udev won't load modules in a specific order, and apparently it's used to load the modules at boot.

There is a way though, it's just slightly more complicated than that. 

Firstly, you do want to add the options to /etc/modules.d/options - add this line (minus quotes):
"options lt_hotswap autoeject=1"

This will allow the module, whenever loaded to detect the lever being released and issue that eject command.

Now, you need to write a small bash script. I called it lt_hotswap.sh:
```

#!/bin/bash

/sbin/modprobe lt_hotswap

```

This script needs to be setuid so:
```

chmod u+s lt_hotswap.sh

```

copy this file into the /etc/init.d directory, then issue the command
```

sudo update-rc.d lt_hotswap.sh defaults

```

and there! Now you should be loading it on boot, with no more not being able to swap your optical drives without freezing!

---

### Post by Whoopie on 2006-08-30
Hi,

you can also add the lt_hotswap module in /etc/modules.

Best regards,
Whoopie

---

### Post by kaens on 2006-08-30
I found out that if you do that, you also need to create a new file in /etc/modprobe.d/ called lt_hotswap containing:

option lt_hotswap auto_eject=1
install lt_hotswap /sbin/modprobe ibm_acpi; /sbin/modprobe --ignore-install
lt_hotswap

if you just put it in /etc/modules, it will kill ibm_acpi because udev does not load modules in a specific order (as far as I know) for some reason. I tried putting it there at first, and that's what happened to me. . . if that works for other people, awesome - but I suspect that's mainly luck.

---

### Post by egoldtech on 2006-08-30
thanks for this thread,  My T30, freeeze each time I want to change my DVD to mY CDRW .
I got some error on your How to  ...
eze@eze-laptop:~/Desktop/lt_hotswap-0.3.6$ sudo modprobe lt_hotswap autoeject=1
Password:
FATAL: Error inserting lt_hotswap (/lib/modules/2.6.15-26-386/acpi/lt_hotswap.ko): Unknown symbol in module, or unknown parameter (see dmesg)


will try again .....

---

### Post by kaens on 2006-08-31
whats the output of dmesg | grep lt_hotswap?

---

### Post by Jawalking on 2006-12-26
I too get an error when following this how to.

This is the error that I see] :
```
jawalking@myPad:~/Desktop/lt_hotswap-0.3.6$ sudo modprobe lt_hotswap autoeject=1
Password:
FATAL: Error inserting lt_hotswap (/lib/modules/2.6.17-10-generic/acpi/lt_hotswap.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

when I check the dmesg this is what I get:
```
jawalking@myPad:~/Desktop/lt_hotswap-0.3.6$ dmesg | grep lt_hotswap
[17267259.232000] lt_hotswap: Unknown parameter `autoeject'
[17267288.824000] lt_hotswap: Unknown parameter `autoeject'

```

Unfortunately this means nothing to me.](*,)  I did open the lt_hotwap.ko file, but half of it was unreadable.

I am new to linux, and would appreciate any help. it would be nice not to have to reboot every time I want to use the extra battery.

---

### Post by SS2 on 2007-01-24
Hi folks,

> **kaens said:**
> 
If everything went fine, we should be in business. To see what this adds, do this:

```
cat /proc/acpi/ibm/bay
#release the eject lever
cat /proc/acpi/ibm/bay
#should still be the same - push the lever back in
sudo modprobe lt_hotswap autoeject=1
cat /proc/acpi/ibm/bay
#release the eject lever
cat /proc/acpi/ibm/bay
#sweet.
```

There is a small mistake there. Instead of typing autoeject=1, I'd rather try it with auto_eject=1. ;)

---

### Post by Arsecroft on 2007-07-17
Thank you kaens!

By the way, when I looked at /proc/version I saw that it had the kernel version with "-generic" appended, but the linux source package doesn't have it. 
> sudo apt-get install linux-source
worked for me, though.


> uname -r 
gives you the information, without the extra newb-confusing info in /proc/version.

EDIT: > change line 1 of lt_hotswap.c from linux/config.h to linux/autoconf.h (config.h is deprecated from 2.6.19). 


Assuming you're running feisty, your kernel will be 2.6.20

ANOTHER EDIT: looks like your syntax for /etc/modprobe.d/lt_hotswap was a bit off.

> options lt_hotswap auto_eject=1
install lt_hotswap /sbin/modprobe ibm_acpi; /sbin/modprobe --ignore-install lt_hotswap


---

