---
title: "Installing Ubuntu from Parted Magic USB"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mayankleoboy1 on 2012-03-03
Hi,

I have a system with Win7 installed. i have downloaded ubuntu 11.04 iso.
i have a 200mb USB drive with bootable parted magic installed.
How can i install Ubuntu from within Parted-Magic environment on my hard drive?
In other words, how to install Ubuntu on a HDD,  from a removable linux environment? 

The basic problem is that the usb is too small to make a live usb.

---

### Post by Double.J on 2012-03-03
Hi there, welcome to the forums!

The easiest way would be to use the minimal CD - this is a minimal installation image that you can copy to USB just as the live environment, but that will download the OS as it installs it. You can get the correct mini ISO from [here]("https://help.ubuntu.com/community/Installation/MinimalCD") be sure to check that you download the version of ubuntu you want - 11.10 Oneiric is the most resent and 10.04 lucid is the LTS.

It is posible to use the parted magic usb to copy the necessary files from an iso image to a hard drive partition so that the installer can be booted from the hard drive... but given how easy it is to flash the stick i can't see the point myself - lots of hassle!

Hope it helps!

---

### Post by Bucky Ball on 2012-03-03
Not sure I follow; you don't have an optical drive (CD) in the computer?

---

### Post by mayankleoboy1 on 2012-03-03
i dont have an optical drive in my computer. 

@ gnu/mirow:
>  It is posible to use the parted magic usb to copy the necessary files  from an iso image to a hard drive partition so that the installer can be  booted from the hard drive... but given how easy it is to flash the  stick i can't see the point myself - lots of hassle!

this is **exactly **what i want to do!
i want to know how to extract the iso on to a HDD partition and make that partition bootable, so that the i can restart and boot from that HDD partition , and install Ubuntu.

---

### Post by audiomick on 2012-03-03
I had a look around, as that topic of booting from an .iso interests me a bit. All of the stuff I found
(search "boot .iso in the Ubunut Documentation, for instance) refers to ways of doing this via a grub menu.

You could of course install a grub on your machine. That should still boot the Windows, even if there is no Linux on there, as far as I know. Thing is, you need an install medium to install the grub that you want to modify to boot from the .iso. I have a feeling that it is a bit of a "chicken or the egg" situation, like the boot process itself.

Your easiest way, if it is at all possible, would probably be to go an get a slightly bigger USB stick and make an installer on that. I managed to make an installer out of a 1GB USB stick I have. I had to tell the USB installer creator to not enable persistance, but having done that, it worked, even though Ubuntu says you need a minimum 2GB.

Having said that, the last time I tried to buy a stick, the smallest one in the shop was about 8GB, I think.

---

### Post by Bucky Ball on 2012-03-03
You download the iso, make a bootable CD or USB with it, boot from that and it will give you an options screen where you can 'Try Ubuntu', 'Install Ubuntu' (to your hard drive), and a number of other options. Still confused about booting from the ISO. Are you just wanting to install Ubuntu to your hard drive?

---

### Post by mayankleoboy1 on 2012-03-03
> **Bucky Ball said:**
> You download the iso, make a bootable CD or USB with it, boot from that and it will give you an options screen where you can 'Try Ubuntu', 'Install Ubuntu' (to your hard drive), and a number of other options. Still confused about booting from the ISO. Are you just wanting to install Ubuntu to your hard drive?

Uptill now i have been using Ubuntu with WUBI.
Now i decided to have a proper install along with Windows.

---

### Post by NikTh on 2012-03-03
> **mayankleoboy1 said:**
> Uptill now i have been using Ubuntu with WUBI.
Now i decided to have a proper install along with Windows.

Ok. So , uninstall your wubi from inside windows , like any other application(Control Panel) . Then create a bootable usb from inside windows with a program like unetbootin and your .iso. and you are done. Boot from usb and install ubuntu.

---

### Post by Bucky Ball on 2012-03-03
> **NikTh said:**
> ... create a bootable usb from inside windows with a program like unetbootin and your .iso. and you are done.

Not so. OP only has 200mb USB dongle. Need to make CD. Much simpler anyhow. ;)

---

### Post by audiomick on 2012-03-03
> **Bucky Ball said:**
> . Need to make CD. Much simpler anyhow. ;)

Except that a USB installer runs faster. And there's this:

> **mayankleoboy1 said:**
> i dont have an optical drive in my computer. 

---

### Post by mayankleoboy1 on 2012-03-03
> **audiomick said:**
> Except that a USB installer runs faster. And there's this:

which brings me back to my original question :  how to extract and install ubuntu from a partedmagic(or any other portable usb linux)  usb?

---

### Post by NikTh on 2012-03-04
The only idea i have in mind right now , is to download the .iso from minimal CD --> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and try to install . I don't think that this will succeed but you have nothing to lose (except parted-magic).

I don't think that you can install a Distro from another Distro's Liveusb. I'm not sure but i think you can't .

---

### Post by Double.J on 2012-03-04
> **NikTh said:**
> The only idea i have in mind right now , is to download the .iso from minimal CD --> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and try to install . I don't think that this will succeed but you have nothing to lose (except parted-magic).

I don't think that you can install a Distro from another Distro's Liveusb. I'm not sure but i think you can't .

I already suggested the alternate minimal CD in my first post I'm afraid, the OP couldn't in flashing this to his usb - he wants to keep parted magic on the usb stick.

(BTW if I'm wrong with that, use unetbootin -or dd if you still have wubi- to copy the minimal CD to the usb install and then put parted magic back on after)

If your situation has changed and you can borrow a cd, larger usb, or stick the hard drive in a different machine to install, you can copy the wubi install over to a full install using this guide

[bcbc's migrate guide]("http://ubuntuforums.org/showthread.php?t=1519354")

When it comes to installing a distro from a live environment (or a full hard drive install for that matter), then NikTh's got a point, it can get a bit distro specific in that it's up to each distro to supply tarballs to let you do it - for example distros such as gentoo and debian can be easily installed onto a hard drive by any linux system installed or live. However ubuntu doesn't have these taballs.

You may be able to install via [lubi]("http://lubi.sourceforge.net/lubi.html"); You would have to mount a partition on the hard drive from parted magic, save the lubi taballs there, extract them there, then download the ubuntu iso to that location and try running the scripts to see if they work.

If you have no luck with lubi, then you can try [this guide]("https://help.ubuntu.com/community/Installation/FromAnotherDistro") 

However As I say I seriously recommend downloading the minimal CD  I mentioned from my first post, write that to the USB, boot, install, then put parted magic back on after.. it really is a lot easier!

Hope it helps!

---

### Post by mayankleoboy1 on 2012-03-04
i guess its a lot easier to do the normal live-cd install than otherwise. so will choose that method.
thanks guys for the answers.

---

