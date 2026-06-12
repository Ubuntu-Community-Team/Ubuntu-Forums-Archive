---
title: "Two quick questions"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-01-26
First question: Can I use a CD-RW for a live CD? I have so many of these laying around, and they don't seem to work for anything else. Will these work as well as CD-R for Ubuntu 11.10 live cd? Anyone used them?

Second: I've never created a bootable USB stick. I have an 8gb one, and I'm sure I'd be able to create one with that Ubuntu bootable usb software, but would I be able to keep using the USB after that for normal file managing? Or would I have to re-format it for normal use, as opposed to booting?

---

### Post by carl4926 on 2012-01-26
1. Yes, so long as it is big enough cd/rw are smaller than cd -r

2. Unetbootin is usually the easiest and typically I only use the USB drive for one thing at a time, so when I'm done I format it for normal use.

---

### Post by lswb on 2012-01-26
I have seen some older systems with CD drives that would not boot from a CD-RW disc but worked OK with a CDR. Anything less than 10 or so years old should work with either.

---

### Post by |{urse on 2012-01-26
I'll second what lswb said, older drives will give you problems sometimes with bootable cd/rws

If you are running windows and considering switching to ubuntu but are out of cd-r/dvd-r heres another super easy way to install ubuntu or a just about any distro to usb.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

That little program will download the iso for whatever distro you want and install it to usb for you.

---

### Post by Thrashrokz33 on 2012-01-26
> **|{urse said:**
> snip

I see how easy that program is to use, and I think I'm just going to make a bootable usb, but I have one quick question. Plugging in my usb assigns it as the I: drive, yet in that program it says "Be careful" when selecting any drive above G:. Why is this? Should I not format the usb while it's on the I: drive?

---

### Post by |{urse on 2012-01-27
nah it's k, Just look in mycomputer real quick and make sure that is actually the usb drives letter.

Thrash does indeed rock btw \\:D/

---

### Post by mastablasta on 2012-01-27
linux live USB creator is even easier to use. though work only in windows.: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
it will install linux (ie. create live USB) and after you are done testing the linux distro you can choose uninstall and then install a new one. all your other files on the USB remain there. no need for some extra partition etc...

---

### Post by |{urse on 2012-01-27
Idk, so far as easy they're about the same, lili is much prettier and has a vm, i'll give it that. Both stay current with ubuntu releases. :)

---

### Post by Mark Phelps on 2012-01-27
> Second: I've never created a bootable USB stick.

My suggestion is to download and use the Universal USB Installer from PendriveLinux.com.  I've had a lot better results using that to create working USB installers than with using unetbootin.

---

### Post by Bartender on 2012-01-27
I was [asking]("http://ubuntuforums.org/showthread.php?t=1914974") about USB drives recently.  Mark Phelps helped out on that thread too.

STAGE 1: I wasted several hours with unetbootin and Ubuntu Start-up Disk Creator.  It turned out that the thumb drive I was using just wasn't gonna work.  I don't know why that is, but clearly some thumb drives work better than others.

STAGE 2: I fired up a W7 laptop and downloaded the PenDrive app.  I could not get it to recognize several current Mint and Ubuntu LiveCD's.  It looked like a download would work fine, but I was skunked trying to use existing LiveCD's.

STAGE 3: I went back to Ubuntu Start-up Disk Creator.  Using a different thumb drive, I was able to create a thumb drive that booted.

So, you have at least 3 main options.  PenDrive on a Windows PC, or unetbootin (download from repos and then open the app) or the built-in Ubuntu Start-up Disk Creator (USUDC).  From what I've seen, some people recommend using USUDC from the LiveCD.  But I just ran it from our installed desktop (10.04).

---

