---
title: "Intel cards with broken EEPROM / e100 driver"
date: 2007-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Stone123 on 2007-04-01
**Please do no use this to upgrade system or for  install it will break, corrupt it. **
Well at last they kernel people let us make our own mistakes. They did't allow  broken ethernet cards that could break your system.

2  simple steps :

1.open terminal (gnome alt+f2)  and type:

> echo "options e100 eeprom_bad_csum_allow=1" | sudo tee -a /etc/modprobe.d/options
Save and exit.
 2. ethernet cards are loaded from initrd so you need to update that to get it on boot time:

>  sudo update-initramfs -u

And thats it reboot.
Thanks to people at #ubuntu-kernel " freenode
/updated  thx to** bruing**
[B]
Ubuntu installation :[/B]

Installing Ubuntu with broken EEPROM:

On Live CD , it's simple . Just boot the CD and start a terminal ,
on alternative , let it  configure keyboard and when it trys to configure network and you get error press <Go back>
Scroll down in menu and  choose start shell.

In Terminal/shell type :
> modprobe -r e100
and then :

> modprobe e100 eeprom_bad_csum_allow=1

type exit to exit shell.

---

### Post by bruenig on 2007-04-02
Pretty sure that will give you a permission denied error. Either
```
sudo bash -c 'echo "options e100 eeprom_bad_csum_allow=1" >> /etc/modprobe.d/options'
```
or
```
echo "options e100 eeprom_bad_csum_allow=1" | sudo tee -a /etc/modprobe.d/options
```
should work though.

Then of course
```
sudo update-initramfs -u
```

---

