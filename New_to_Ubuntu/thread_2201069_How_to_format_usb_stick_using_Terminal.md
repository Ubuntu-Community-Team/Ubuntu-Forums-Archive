---
title: "How to format usb stick using Terminal?"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-22
How do you format a usb stick with ext4 file system using the Terminal?

---

### Post by sudodus on 2014-01-22
I think the easiest way is to use gparted, but if you don't want or cannot use a gui program there are fdisk, cfdisk and parted, which are text based programs. cfdisk is easiest to use and parted the most advanced of the programs. Read the manual pages

```
man fdisk
man parted
```

and search for tutorials and tips via the internet. I think the programs have a help command, that gives you a quick output of avalable commands.

---

### Post by Gone fishing on 2014-01-22
firstly to list your partition information to find the name of the device / partition you want to format

sudo fdisk -l

Then

sudo mkfs.ext4  /dev/sdc?

changing /dev/sdc? as needed

---

### Post by bc.haynes on 2014-01-31
I did as you said:
```
sudo fdisk -l

sudo mkfs.ext4 /dev/sdc
```

My USB stick was sdc. I first got an error message;
> /dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n)
I answered y and got this error:
[quote]

Nevermind

---

### Post by rawrmonster on 2014-01-31
No you are targeting the whole device instead of the partition. try the command "dmesg | grep /dev/sdc" with out the quotes. it should return with something like /dev/sdc1 or something like that. After you get that info with the number on the end type what your terminal said with that command. "sudo mkfs.ext4 /dev/sdc1" or what ever your terminal said the device name was.

---

### Post by bc.haynes on 2014-01-31
Thanks,y'all.

---

