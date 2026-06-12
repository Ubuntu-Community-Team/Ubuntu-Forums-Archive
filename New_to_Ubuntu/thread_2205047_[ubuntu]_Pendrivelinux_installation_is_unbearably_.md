---
title: "[ubuntu] Pendrivelinux installation is unbearably slow"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by Ultimatefry on 2014-02-11
Hello! I recently used pendrivelinux to make an installer to add Ubuntu 12.04 to another, larger flash drive. This is the 64-bit version on a brand new computer, yet it is nightmarishly slow. I installed it 3 times before it would log me in in a timely manner. What could be going wrong?

---

### Post by Bill Tetzeli on 2014-02-11
IMHO you're doing nothing wrong.  A flash drive is great for archiving data, but horrible to run an OS on (unless it's incredibly lightweight).  They're just much slower than internal HDs, that's all.  I tried installing an Ubuntu-based distro to a flash thumb drive not long ago and it was tortuously slow.

---

### Post by monkeybrain20122 on 2014-02-11
How much ram do you have? Since live usbs run entirely in ram if you don't have too much ram it would be slow.

---

### Post by Dennis N on 2014-02-11
You have a bottleneck with the read/write speed of the flash drive. This kind of installation works best with USB 3.0 port and USB 3.0 flash drive. Even better is to use an external USB hard drive.

---

### Post by monkeybrain20122 on 2014-02-11
> **Dennis N said:**
> You have a bottleneck with the read/write speed of the flash drive. This kind of installation works best with USB 3.0 port and USB 3.0 flash drive. Even better is to use an external USB hard drive.

There is, but still wouldn't be "nightmarishly slow". I find the live usb usually quite fast if you just do light stuffs unless it is some old machine with not enough ram.

---

### Post by Ultimatefry on 2014-02-11
Yeah, I'm thinking to just add it on to my computer, and then suddenly...my BIOS refuses to recognize Windows Boot Loader in any mode.

---

### Post by Dennis N on 2014-02-11
> **monkeybrain20122 said:**
> There is, but still wouldn't be "nightmarishly slow". I find the live usb usually quite fast if you just do light stuffs unless it is some old machine with not enough ram.

I read the first post as describing a full install to a flash drive, not a live usb. These really are slow with a cheap USB 2.0 stick.

---

### Post by monkeybrain20122 on 2014-02-11
> **Dennis N said:**
> I read the first post as describing a full install to a flash drive, not a live usb. These really are slow with a cheap USB 2.0 stick.

Oh, I see, I just read "Pendrivelinux". :) Yeah a full install in a usb flash drive would be horridly slow for the reasons you mentioned. An external drive, even smaller (I have done it in something as small as 5Gs) would perform exactly like an installation in the internal drive. Sorry for the misunderstanding.

---

### Post by C.S.Cameron on 2014-02-12
I run my entertainment computer from a flash driive and my second work computer, (email, internet and photo screen saver).
Both systems are fast but I think it is due to having lots of RAM.
The USB2 drives are Sandisk Cruzer Fit 16GB, nothing special.

I would suggest using UNetbootin or Startup Disk Creator to make the Live USB, Lots of people have trouble with the one from Pendrivelinux.

---

### Post by C.S.Cameron on 2014-02-12
> **Ultimatefry said:**
> Yeah, I'm thinking to just add it on to my computer, and then suddenly...my BIOS refuses to recognize Windows Boot Loader in any mode.

Will  it boot to Windows if you leave the USB plugged it? You should be able to fix the bootloader using the Windows install disk.

---

### Post by sudodus on 2014-02-12
> **Ultimatefry said:**
> Yeah, I'm thinking to just add it on to my computer, and then suddenly...my BIOS refuses to recognize Windows Boot Loader in any mode.

What happens if you shut down, wait a minute or two to cold boot the computer? Or is it the problem that C.S.Cameron thinks, when he asks if 'it will boot to Windows if you leave the USB plugged'?

> **Dennis N said:**
> I read the first post as describing a full install to a flash drive, not a live usb. These really are slow with a cheap USB 2.0 stick.

There are really big differences in speed between different USB pendrives. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858") (see all posts)

> **monkeybrain20122 said:**
> Oh, I see, I just read "Pendrivelinux". :) Yeah a full install in a usb flash drive would be horridly slow for the reasons you mentioned. An external drive, even smaller (I have done it in something as small as 5Gs) would perform exactly like an installation in the internal drive. Sorry for the misunderstanding.

> **C.S.Cameron said:**
> I run my entertainment computer from a flash driive and my second work computer, (email, internet and photo screen saver).
Both systems are fast but I think it is due to having lots of RAM.
The USB2 drives are Sandisk Cruzer Fit 16GB, nothing special.

I would suggest using UNetbootin or Startup Disk Creator to make the Live USB, Lots of people have trouble with the one from Pendrivelinux.

A live system (without persistence) is the best option with a slow USB pendrive, but I can confirm that persistent live systems as well as installed systems are quite nice with fast pendrives or USB hard disk drives (even when plugged into USB 2 systems).

---

