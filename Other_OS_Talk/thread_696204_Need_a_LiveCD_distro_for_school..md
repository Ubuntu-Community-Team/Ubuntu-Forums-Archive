---
title: "Need a LiveCD distro for school."
date: 2008-02-13
forum: Other OS Talk
---

### Post by Envergure on 2008-02-13
My tech teacher opens the computer lab at my high school at lunch for people to use.  He says I can run Linux from a LiveCD, but because of the school board being paranoid we have to be disconnected from the network to do it (they're worried we'll go cracking through the network, I guess).

No network means no Internet, which means no downloading packages.  I want to have packages and files there at my disposal that aren't on the LiveCD by default.

Can I create a LiveCD with a customized combimation of packages on it?  Alternatively, I have a 2GB Flash SSD.

I wouldn't be using Ubuntu there, just because by the time it loaded from the CD lunch would be half-over.

So I'm looking for either a LiveCD distro that comes with build packages or one that can be installed on a Flash drive.

---

### Post by init1 on 2008-02-13
Debian Live is perfect for this. The Live-Helper allows you to create bootable CD with as few or as many packages as you want. The only way I've been able to get live-helper to build the ISO however is with pure Debian, and not with Ubuntu. 
[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)
The instructions for getting Live-Helper are old, so I'd either get the [Etch backport]("http://packages.debian.org/etch-backports/live-helper") or 
```

apt-get install live-helper

```
if you're in Lenny. So in either case skip
> 
Downloading and installing Live-Helper:

1. Open a terminal and type sudo gedit /etc/apt/sources.list

    Add deb [http://live.debian.net/debian/](http://live.debian.net/debian/) etch main to the list and save the file.

2. Back at the terminal, type sudo apt-get update
3. Type sudo apt-get install debian-unofficial-archive-keyring
4. Type sudo apt-get install live-helper

because last time I checked they no longer worked.

---

### Post by Pogeymanz on 2008-02-13
Puppy, Puppy or Puppy.

Puppy Linux has a lot of useful packages right from the start, including seamonkey web browser, various text-editors, picture veiwers and lots of stuff I never use, but I'm sure is good. It also looks nice, is easy to use and is only 100MB.

Also, you can boot it into RAM, meaning you can take the CD out and use that drive. It will also run faster when it's in RAM.

---

### Post by mrsteveman1 on 2008-02-13
You can in fact put the livecd onto a flash drive and then install things on top of it, it will function somewhat like the eeepc does, the base system will be read only and then unionfs will be used to let you change things and write over stuff. Its persistent and will act like a normal system when done right. I might also add that running the livecd from a USB drive is SIGNIFICANTLY faster than booting from the CD due to the fact that SSDs are whole orders of magnitude faster than CDs at loading random files.

[Heres]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") a tutorial i found specific to 7.10, theres another one on the ubuntu wiki for 7.04 as well if you need it.

---

### Post by smartboyathome on 2008-02-13
> **init1 said:**
> Debian Live is perfect for this. The Live-Helper allows you to create bootable CD with as few or as many packages as you want. The only way I've been able to get live-helper to build the ISO however is with pure Debian, and not with Ubuntu. 
[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)
The instructions for getting Live-Helper are old, so I'd either get the [Etch backport]("http://packages.debian.org/etch-backports/live-helper") or 
```

apt-get install live-helper

```
if you're in Lenny. So in either case skip

because last time I checked they no longer worked.

I looked at the mailing list, and it seems like you need to change some lines to make it work with Ubuntu rather than Debian.

---

### Post by darrelljon on 2008-02-14
See [this list of Educational distros](http://linux.wikia.com/wiki/Category:Educational).
I'd also recommend [Edupup](http://www.edupup.org/).

---

### Post by cardinals_fan on 2008-02-16
I'm in high school myself, but they won't let us use a Live CD :(

Regardless, I recommend [Puppy]("http://www.puppylinux.org"), [SLAX]("http://www.slax.org") (even though it has KDE), or [Zenwalk Live]("http://www.zenwalk.org") (5.0 should be out soon...).

---

### Post by MarCustomized on 2008-02-16
[Wolvix.]("http://wolvix.org/")

---

