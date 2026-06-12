---
title: "USB key to boot Linux"
date: 2018-07-13
forum: New to Ubuntu
---

### Post by Dr. McKay on 2018-07-13
I have a Lenovo E580 15 inch laptop (i7, 16Gb RAM, 512Gb SSD), running Windows 10 Pro 64-bit.

I would like to run Linux on it as well, but don’t care much for a partitioned internal drive.
I would therefore install Linux on a USB 3 key (I assume 3.0 will be enough, 3.1 might be a bit overkill for this usage, or not ?)

I would go for a 256gb drive, to have enough space to work with. But what do I look for when buying such a USB stick ?  I hear that some of those USB sticks are not bootable. 

Any advice on which key to buy ?

---

### Post by #&amp;thj^% on 2018-07-13
This will lead to opinions but I really like these 2>>> [Sandisk Extreme CZ80 USB 3.0]("https://www.amazon.com/dp/B00KT7DOSE?tag=thewire06-20&linkCode=xm2&ascsubtag=AgEAAAAAAAAAAK6R")
And [SanDisk Extreme Go USB 3.1 ]("https://www.amazon.com/dp/B01NARBPI7?tag=thewire06-20&linkCode=xm2&ascsubtag=AgEAAAAAAAAAAJLG")After testing a handful of thumb drives I found the  64 GB SanDisk Extreme CZ80 USB 3.0 Flash Drive offers the best combination of speed, price, capacity, and usability of any thumb drive I have used.
Just my 2 cents worth. Sounds like an Advertisement dosen't it? :)

---

### Post by mIk3_08 on 2018-07-13
> **Dr. McKay said:**
> I have a Lenovo E580 15 inch laptop (i7, 16Gb RAM, 512Gb SSD), running Windows 10 Pro 64-bit.

I would like to run Linux on it as well, but don’t care much for a partitioned internal drive.
I would therefore install Linux on a USB 3 key (I assume 3.0 will be enough, 3.1 might be a bit overkill for this usage, or not ?)

I would go for a 256gb drive, to have enough space to work with. But what do I look for when buying such a USB stick ?  I hear that some of those USB sticks are not bootable. 

Any advice on which key to buy ?

I hear that some of those USB sticks are not bootable. --

I don't know if there are some USB stick that are not bootable. correct me if Im wrong, I haven't encounter any. I think there a lot of software that can configure USB to become bootable. If this software won't work then maybe the other software can.

---

### Post by C.S.Cameron on 2018-07-13
After a few years I'm still trying to figure out if USB3.0 or 3.1 is any better for booting Ubuntu than USB2.
Ubuntu seems to run well in RAM with USB2, (given enough RAM).

The USB3 flash drives I've tested are:
Lexar S33 64GB - Will not boot USB3 
Lexar S75 128GB - Will not boot USB3
Sandisk Ultra 32GB - Will not boot USB3 

All of the USB3 hard drives I've tested seem to boot USB3 OK.

---

### Post by sudodus on 2018-07-13
See this link and links from it for suitable USB 3 pendrives,

[FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

If you want a persistent live system, you can create it with [mkusb](https://help.ubuntu.com/community/mkusb).

If you want an installed system (installed like into an internal drive), you can do it according to the following link, 

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

or if you ask @C.S.Cameron, you can get some more links by him for that purpose.

---

### Post by oldfred on 2018-07-13
I have just been using MicroCenter's own housebrand flash drives. I did find with my old BIOS system that using a USB3 flash drive was about 10% faster in USB2 ports than USB2 flash drives, so I converted long before I even had a system with USB3 ports.

But I also had an old SSD (Microcenter again) that I used in my old BIOS system. I purchased a USB3 to SATA adapter and found that to be almost as fast as my internal drives and a lot faster than my USB3 flash drives.

MicroCenter is only a couple of miles away. I have to restrict my visits as when you check out they have the flash drives behind counter and every time I visit it seems they are lower in cost or same cost for larger capacity. Or I have a lot of flash drives of various sizes. Newer 64GB ones are all full installs for emergency boot in smaller / (root) and rest for data.

---

### Post by oldrocker99 on 2018-07-13
Oddly, every USB stick I have used has booted fine.

Maybe I'm just lucky...

---

### Post by patk1212 on 2018-07-13
I am a relative newbie.  I used this:

[https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

to install 16.04 onto a Sandisk 32GB usb drive and it worked fine!

---

### Post by TheFu on 2018-07-13
I've found that the flash drive and USB controller seem to interrelate and determine whether booting will work or not.  I've had name brand flash drives work on some systems, but not others.  I've had the same with cheap flash drives. I've also had systems refuse to boot anything off USB3 ports, but work fine for USB2.

Wish I could say X always boots on Y, but that hasn't been what I've seen.  My group of flash drives is fairly small, only about 15, so YMMV.

On one of my laptops, it is easiest to just boot from the SDHC slot.

I'm not a fan of using flash drives for daily running any OS. I've had too many fail unexpectedly.  Would recommend using an external SSD, if possible.  64G is huge for Linux - here's my laptop using a 64G SSD.
```
/dev/mapper/ubuntu--vg-root   51G   32G   17G  66% /
```
That's 17G free, BTW. My HOME is inside /.

---

### Post by mIk3_08 on 2018-07-13
> **sudodus said:**
> See this link and links from it for suitable USB 3 pendrives,

[FromUSBStick#Prerequisites]("https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites")

If you want a persistent live system, you can create it with [mkusb]("https://help.ubuntu.com/community/mkusb").

If you want an installed system (installed like into an internal drive), you can do it according to the following link, 

[Boot Ubuntu from external drive]("https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312")

or if you ask @C.S.Cameron, you can get some more links by him for that purpose.



Thanks for the new info sudodus. This will help a lot.

---

### Post by Skaperen on 2018-07-13
> **oldrocker99 said:**
> Oddly, every USB stick I have used has booted fine.

Maybe I'm just lucky...

2 of us are lucky.  i just (do the equivalent of) dd the iso image to the memory stick device.  be careful trying that ... a small typo can ruin you day (and all your data).

---

### Post by TheFu on 2018-07-14
> **Skaperen said:**
> 2 of us are lucky.  i just (do the equivalent of) dd the iso image to the memory stick device.  be careful trying that ... a small typo can ruin you day (and all your data).

Generally, I use dd too, but about 5% of the time, I'll use yumi on (cough) Windows to setup multi-boot.  Haven't had any luck using any other multi-boot tools.  Most of my installs are into virtual machines, so making a flash drive isn't all that common.

---

### Post by Dr. McKay on 2018-07-14
I tested with a generic USB2 key (8Gb). Downloaded the Ubuntu image and did the install onto the USB key using Unetbootin in Windows. Worked fine, although I found the experience a bit slow.

THe Kingston HyperX Savage USB 256 GB seems to be good...

---

### Post by C.S.Cameron on 2018-07-14
When installing to USB I like a system that boots either UEFI or BIOS, and has a partition that can be used by both Linux and Windows.
An easy way to make such a device is to start with a **mkusb** Persistent install and then install Ubuntu over the ISO9660 and casper-rw partitions.

See > [https://askubuntu.com/questions/1051543/how-to-make-a-live-ubuntu-18-04-usb-with-a-persistent-storage-of-more-than-4gb/1051558#1051558](https://askubuntu.com/questions/1051543/how-to-make-a-live-ubuntu-18-04-usb-with-a-persistent-storage-of-more-than-4gb/1051558#1051558)

---

### Post by mIk3_08 on 2018-07-15
SanDisk Ultra USB 3.0 Flashdrive is fine

---

### Post by TheFu on 2018-07-15
> **mIk3_08 said:**
> SanDisk Ultra USB 3.0 Flashdrive is fine

I think people misunderstand. Without posting the USB control chips, there isn't any way to say that any specific flash is or isn't bootable.  It is the combination of those things, not just the flash storage components.

---

### Post by sudodus on 2018-07-15
> **TheFu said:**
> I think people misunderstand. Without posting the USB control chips, there isn't any way to say that any specific flash is or isn't bootable.  It is the combination of those things, not just the flash storage components.

+1

Most USB pendrives work with most USB systems, but there are many exceptions, and they are difficult to predict.

---

### Post by mIk3_08 on 2018-07-15
> **TheFu said:**
> I think people misunderstand. Without posting the USB control chips, there isn't any way to say that any specific flash is or isn't bootable.  It is the combination of those things, not just the flash storage components.

yes, it is bootable. I have SanDisk Ultra 8GB USB 3.0 Flashdrive here. I usually used it for fresh Ubuntu installation.
sorry TheFu for not giving the specification that this thread needs.

> **sudodus said:**
> +1

Most USB pendrives work with most USB systems, but there are many exceptions, and they are difficult to predict.

Thanks a lot sudodus... That is exactly what I meant. Thumbs up!

---

### Post by C.S.Cameron on 2018-07-23
I've been a little horrified to find out TLC is only good up to 1000 writes.
Deponia, SanDisk Professor says all Samsung flash drives are MLC, (however they invented TLC?). [http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/How-to-know-which-SanDisk-flash-drives-use-MLC-NAND-and-which/td-p/353259](http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/How-to-know-which-SanDisk-flash-drives-use-MLC-NAND-and-which/td-p/353259)
Current web articles are now saying MLC is good for 1000 to 10000 writes.
Many SSD's are MLC.
It is difficult to find out who is admitting manufacturing TLC drives, these are probably all the bargain drives, (the ones that brick the day after the 30 day warranty runs out).
3D TLC NAND seems to be gaining popularity for low end flash drives the lifetimes are in the hundreds of writes.
SLC still has the highest endurance, 1000000's of writes and is fastest but prices are high.

---

