---
title: "HP printing problems"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by woody1 on 2008-05-27
Using Hardy Heron with an HP Photosmart 7450 with the hp driver ver 2.8.2+2.8.2-Oubuntu8 (HP 7400 series). This is not reliable sometimes it works fine, then it will print the first document maybe and then go into sulk mode.HP Device manager says printing, printer icon on taskbar has a no entry sign on it announcing a media jam. I have tried the printer on a separate machine running Windows 98, this works fine!! I have tried the printer plugged into an add on usb hub (i.e. card plugged into a pci slot).
I have downloaded and installed the latest updates.
Any advice on how to proceed further would be appreciated

---

### Post by miked2 on 2008-06-27
Here's a bodge that might help.  
I've been having the same problem (I have the same printer).  
I tried getting the latest hplip binary from the hp website but this didn't give any improvement.  After reading through a few bug reports, I found that someone has mentioned a temporary solution to a similar problem: 
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/181242/comments/41]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/181242/comments/41")
which seems to have got my printer working for now.  
What I did was 
```
sudo gedit /etc/udev/rules.d/55-hpmud.rules
```

then replaced owner root with my username. 
I believe that one of the problems is a permissions issue, which this seems to get around.  
I'd be interested to know if anyone can suggest a neater way to fix this.

---

### Post by woody1 on 2008-07-17
Thanks for your suggestion, I'll certainly give it a go.

---

### Post by ramjet_1953 on 2008-07-18
This may be a better modification:

> # Udev rules file for HP printer products.

ACTION!="add", GOTO="hpmud_rules_end"
SUBSYSTEM=="ppdev", OWNER="lp", GROUP="lp", MODE="0666"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="pid_test"
SUBSYSTEM!="usb_device", GOTO="hpmud_rules_end"

LABEL="pid_test"

# Check for AiO products (0x03f0xx11).
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??11", OWNER="lp", GROUP="lp", MODE="0666"
# Check for Photosmart products (0x03f0xx02).
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??02", OWNER="lp", GROUP="lp", MODE="0666"
# Check for Business Inkjet products (0x03f0xx12).
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??12", OWNER="lp", GROUP="lp", MODE="0666"
# Check for Deskjet products (0x03f0xx04).
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??04", OWNER="lp", GROUP="lp", MODE="0666"
# Check for LaserJet products (0x03f0xx17).
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??17", OWNER="lp", GROUP="lp", MODE="0666"

LABEL="hpmud_rules_end"

Regards.
Roger :cool:

---

### Post by woody1 on 2009-02-28
Eventually tried both of these, I get a test page and possibly one or two more before I get a popup message that the printer may not be connected. Wasted far too much time on this, one more go then I'll just use it on a Windows machine.

Thanks for all your help

Woody1

---

### Post by woody1 on 2009-03-02
Found the problem  !!!!!
For some reason the printer did not like the usb hub that I had it plugged into, it is now working as device 3 on bus 3, it did not seem to like bus 4!
, other usb devices work fine on this bus. Very strange!!!

Thanks for your help

---

