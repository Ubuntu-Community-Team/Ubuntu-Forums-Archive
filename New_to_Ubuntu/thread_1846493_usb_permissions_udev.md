---
title: "usb permissions udev"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by b-boy on 2011-09-19
Hi guys

I need help with setting permissions for a usb printer with udev. The printer only works if I change permission to BOTH the bus and the device manually.

I pick up the device and bus with lsusb

```
Bus 003 Device 002: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C
```

I then need to change permissions

```
chown root:users /dev/bus/usb/003/ -R
```
 

and after this is works can someone please help with a udev rule to do this

---

### Post by anewguy on 2011-09-19
So, if you lp some simple text file as your regular userid does it find it or does it give you a permissions error?

If it gives you a permissions error, try sudo lp filename - if that works then it's definitely udev and the rule file would be:



# Seiko Epson Corp. Receipt Printer M129C udev rules file
#
# The 90-M129C.rules file is used to set the ownership of the M129C
# receipt printer

ACTION!="add", GOTO="M129C_rules_end"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="pid_test"
SUBSYSTEM!="usb_device", GOTO="M129C_rules_end"

LABEL="pid_test"

# Check for the M129C receipt printer and set to lp group with world access
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0202", GROUP="lp",[COLOR="Red"]remove:  ENV{ID_HPLIP}="1"  [/COLOR]MODE="0666"

[COLOR="Red"]#
# Now find the device, then set the permission
#

  dev="$(basename "$DEVNAME")"
  bus="$(basename "$(dirname "$DEVNAME")")"

# as is, the ownership of the entire bus will go to root:users
# can't use bus and device as it seems to be
# overruled by the rule above, otherwise the dev would be added
# to the command:  su "chown root:users "${bus}${dev}" -R"
# this is according to my log file anyway

  su "chown root:users "${bus}" -R"
[/COLOR]

LABEL="M129C_rules_end"




This will add the printer to the "lp" group and with world access (0666).  As a result, I think the bus entry should be set correctly then also, but you'll have to try it and see.

Call this file 90-M192C.rules and put it in /etc/udev/rules.d

Be sure to change to only root as the owner, only root with read access

Reboot (shouldn't be needed but I prefer it anyway).

See if you can access the printer.

Dave ;)

---

### Post by b-boy on 2011-09-19
@anewguy thanks it does change the device to lp but not the bus and if the bus is not changed it does not work.

---

### Post by anewguy on 2011-09-19
Made a change in the rule file - it's in red in my original post.  I've done the original part of the rule many times so I knew how to do that.  The bus and device where a new animal to me so I can't guarantee it will work the first shot - we may need to do a little playing around.

In the mean time, I'll see if I can find someway to test that on some USB device on my end - maybe I can do it with one of my external hard drives.

Let me know how it goes, and don't be surprised if it doesn't work the first time.

Dave ;)

BTW - I have the chmod to the entire bus as you had.  If you have any other devices on that USB bus the ownership changes as well.

---

### Post by b-boy on 2011-09-20
Thanks Dave I really appreciate the effort. I have managed to get it working with some help from a friend

here is my udev rules that runs a script

```
SUBSYSTEM=="usb", ACTION=="add", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0202", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", GROUP="users", MODE="0664", RUN+="/usr/bin/hack_epson_tm-t70_perms.sh"
```

the script

```
#!/bin/sh

test "$ACTION" = "add" || exit 0

DIRNAME="/dev/bus/usb/$BUSNUM"

echo "DIRNAME \"$DIRNAME\"" >> /tmp/epsonlog

chgrp users "$DIRNAME"
chmod 775 "$DIRNAME"
exit 0
```


Though I must say I think I will try you method as well.

---

### Post by anewguy on 2011-09-20
I'm glad you got it working.  If you do by chance try the changes I had, let me know if they work or not - like I said I'm not sure.

Good luck!

Dave ;)

---

