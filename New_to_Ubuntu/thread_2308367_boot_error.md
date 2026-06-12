---
title: "boot error"
date: 2016-01-02
forum: New to Ubuntu
---

### Post by kranthi4 on 2016-01-02
hi i'm new here, i tried to boot from usb then it says not com32 img

---

### Post by oldos2er on 2016-01-02
System specs? Ubuntu version? Did you [checksum the *.iso]("https://help.ubuntu.com/community/HowToMD5SUM")? Please give people some information to work with if you expect real help.

---

### Post by tea for one on 2016-01-02
> **kranthi4 said:**
> hi i'm new here, i tried to boot from usb then it says not com32 img

Is this an Ubuntu 15:10 image you are trying to boot?

Is the exact error message as follows:-

gfxboot.32: not a COM32R image (appearing as white text on a black background)

Try this when you see the message:-

Press the tab key and you should see "live live-install..........etc

Type "live" and you should then arrive at a live Ubuntu session.

However, on a side note, oldos2er is correct to suggest that you should offer more pertinent information to encourage accurate responses.

Let us know how you get on?

---

### Post by sudodus on 2016-01-02
> **kranthi4 said:**
> hi i'm new here, i tried to boot from usb then it says not com32 img

Welcome to the Ubuntu Forums :-)


1. Check that the download was good (as suggested by *oldos2er*).


2. and please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it easier to give good advice.


3. I think another tool would work better to create the USB boot drive (or use the work-around suggested by *tea for one*)

You find tips at the following link and links from it

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by kranthi4 on 2016-01-02
sorry for late replay, it was night here, it is as u said but nothing is happening in fact keyboard is not functioning even in grub for some reason
by the way my system  is lenovo aio c320,Pentium processor,2gb ram, realteach network card

---

### Post by sudodus on 2016-01-03
According to the general specification, it should work with standard Ubuntu and any Ubuntu flavour, Kubuntu, Lubuntu, ... Xubuntu. I have no experience of Lenovo AIO computers, but other IBMs and Lenovos (except the very newest) work well with linux.

- ***Which iso file*** did you download (name of the file)?

- Have you checked with ***md5sum*** that the iso file was downloaded correctly?

- Have you tried ***another tool*** to flash the iso file to the USB pendrive? Will you do it is Windows or linux? See [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by kranthi4 on 2016-01-03
ubuntu-15.10-desktop-i386.iso
i used startup disk creator

---

### Post by sudodus on 2016-01-03
The Startup Disk Creator is buggy in the current versions, but it will get a new engine under the hood in the next version, 16.04 LTS to be released in April. It will clone the iso file to the pendrive, similar to the method used by mkusb.

-o-

Please check that the download was correct. Run the following command in a terminal window and check if you get the correct checksum

```
md5sum ubuntu-15.10-desktop-i386.iso
7d483b990de4e1369b76b7b693737191  ubuntu-15.10-desktop-i386.iso
```

Try mkusb instead of the startup disk creator. See the following link

[mkusb](https://help.ubuntu.com/community/mkusb)

You get it via the PPA with the following commands

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

---

### Post by kranthi4 on 2016-01-04
pressing tab worked for me

---

