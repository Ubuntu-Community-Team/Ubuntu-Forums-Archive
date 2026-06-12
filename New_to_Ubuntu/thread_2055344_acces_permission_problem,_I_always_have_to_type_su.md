---
title: "acces permission problem, I always have to type sudo password"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by gam01hr on 2012-09-09
situation is:
--------------
1/ I have installed a program 'avrdude' into '/usr/bin/avrdude' by Ubuntu software center
2/ If I run 'avrdude' as sudo, I get no error.
```
$ sudo avrdude -p m16 -c dragon_jtag -P usb -U flash:r:output.hex:h

avrdude: AVR device initialized and ready to accept instructions

Reading | ################################################## | 100% 0.01s

avrdude: Device signature = 0x1e9403
avrdude: reading flash memory:

Reading | ################################################## | 100% 1.58s

avrdude: writing output file "output.hex"

avrdude: safemode: Fuses OK
```avrdude done.  Thank you.
3/ If I run 'avrdude' without sudo, I get the error.
```
$ avrdude -p m16 -c dragon_jtag -P usb -U flash:r:output.hex:h
avrdude: usb_open(): cannot read serial number "error sending control message: Operation not permitted"
avrdude: usb_open(): cannot read product name "error sending control message: Operation not permitted"
avrdude: usbdev_open(): error setting configuration 1: could not set config 1: Operation not permitted
avrdude: usbdev_open(): did not find any USB device "usb"
```situation should be:
--------------
1/ I want to use Ubuntu without the need almost always type the sudo because it slows me down.

2/ I tried to change the owner of 'avrdude' but it didn't solve my problem
/usr/bin$ chown -hR catwalk ./avrdude

:KSPlease is there some clever solution, other then logging in Ubuntu as root at startup?

I use Ubuntu 12.04 LTS

---

### Post by arpanaut on 2012-09-09
Give this a read.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by NikTh on 2012-09-09
> **gam01hr said:**
> 
1/ I want to use Ubuntu without the need almost always type the sudo because it slows me down.

2/ I tried to change the owner of 'avrdude' but it didn't solve my problem
/usr/bin$ chown -hR catwalk ./avrdude

:KSPlease is there some clever solution, other then logging in Ubuntu as root at startup?

I use Ubuntu 12.04 LTS

It would not be a clever solution to bypass or disable sudo. It would be a big security hole in your system. 

For specific programs you can bypass sudo with simple scripts. 

e.g for the program of your example. avrdude

```
nano avrdude.sh
```place this content inside
```
#!bin/bash 

echo "your password here" | sudo -S sudo /usr/bin/avrdude
```save with Ctrl+X , then Y(es) and then Enter(key).

give to the script X-ecute permissions 

```
chmod a+x avrdude.sh
```and remove R-ead W-rite permissions from Others and Groups.

```
chmod og-rw avrdude.sh
```now execute the script to see if meet your needs 

```
./avrdude.sh
```

Thanks

---

### Post by d3v1150m471c on 2012-09-09
> **NikTh said:**
> It would not be a clever solution to bypass or disable sudo. It would be a big security hole in your system...
```
nano avrdude.sh
```place this content inside
```
#!bin/bash 

echo "your password here" | sudo -S sudo /usr/bin/avrdude

```

but leaving your plaintxt passwd in a shell script is definitely not a big security hole. by all means, go right ahead.

---

### Post by satyamM on 2012-09-09
LOL, doing everything without sudo permissions.....

I don't know, is its possible but if possible and you do it, then it would be a serious security issue to your imp. files and softwares of system.

Root user is a very imp.(and very nice) feature in Ubuntu(or Unix) and that what differentiates Unix from Proprietary operating systems. You cant change your basic state of system until you get root's permission. That's what how it is and that's what how it should be.


If you are having lot of work on terminal and always have to type sudo password which might be irritating you, then login as root and then perform tasks.....Else security concerns are there.

Good Luck.

---

### Post by gam01hr on 2012-09-09
thank you for your answer, I'll try it. 
The the reason why I want run 'avrdude' without sudo is that, it is called from make/makefile.
Of course I don't need all rights over my whole desktop.

---

### Post by Wim Sturkenboom on 2012-09-09
Not a sudo specialist, but from 'man sudoers', the following should be possible

```

yourusername ALL = NOPASSWD: /usr/bin/avrdude

```

Use visudo to add the above line to /etc/sudoers.
There might be some side-effects that you want to be aware of, so read 'man sudoers'.

USE AT OWN RISK (and have a liveCD ready in case it goes wrong :))

---

### Post by Cheesemill on 2012-09-09
> **Wim Sturkenboom said:**
> Not a sudo specialist, but from 'man sudoers', the following should be possible

```

yourusername ALL = NOPASSWD: /usr/bin/avrdude

```Use visudo to add the above line to /etc/sudoers.
There might be some side-effects that you want to be aware of, so read 'man sudoers'.

USE AT OWN RISK (and have a liveCD ready in case it goes wrong :))
A couple of points:
If you don't know how to use the vi text editor then you can use the much easier nano:
```
sudo EDITOR=nano visudo
```
It has a handy menu for what the CTRL key does at the bottom of the screen.

Also make sure that you add the declaration in the above post at the bottom of your sudoers file, otherwise it will get overwritten further down in the file leading to unexpected results.

Once your done log out and back in, you can now run the command:
```
sudo avrdude
```
without being prompted for your password.

---

### Post by newb85 on 2012-09-09
> **d3v1150m471c said:**
> but leaving your plaintxt passwd in a shell script is definitely not a big security hole. by all means, go right ahead.

Of course, if read permissions were removed from the file, it would be more secure...

---

### Post by steeldriver on 2012-09-09
Another way to approach it - since it seems the problem is not with the actual execute permission on the avrdude program but more likely with the underlying usb device permissions - might be to write a custom udev rule that creates the device file with UID=user rather than root when the device is plugged in. Or more elegantly, create a group 'avrdude' and set the device file GID - then you can just add any users who need to run avrdude on the device to that group.

I'm a n00b with udevadm but I managed to set something up like that for an experimental usb device recently.

---

### Post by NikTh on 2012-09-09
> **d3v1150m471c said:**
> but leaving your plaintxt passwd in a shell script is definitely not a big security hole. by all means, go right ahead.

> **NikTh said:**
> **[SIZE=3]and remove R-ead W-rite permissions from Others and Groups.[/SIZE]**

```
chmod og-rw avrdude.sh
```now execute the script to see if meet your needs 

Because you probably missed that.

---

