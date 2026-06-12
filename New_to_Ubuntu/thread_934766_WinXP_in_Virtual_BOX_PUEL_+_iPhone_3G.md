---
title: "WinXP in Virtual BOX PUEL + iPhone 3G"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by peterlauri on 2008-09-30
Is there anyone here who have gotten that combination to work? I love my iPhone 3G, but would like to have all the iTunes and stuff under Windows.

When I connect the iPhone the WinXP detects the camera inside of it, and that the iPhone is connected. But the iTunes doesn't detect it somehow.

Please help, I'm getting desperate :(

---

### Post by UbuWu on 2008-10-01
There is a bug in virtualbox preventing this from working:

[http://www.virtualbox.org/ticket/491](http://www.virtualbox.org/ticket/491)

It should be possible to do with vmware though.

---

### Post by callmesid on 2008-10-06
I was able to get my iPhone to sync. My setup:

Ubuntu 8.04 (Hardy Heron)
[VirtualBox 2.0.2]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")
iPhone 3G (Software version 2.1)

I followed the steps mentioned in the thread on the virtualbox website

[http://www.virtualbox.org/ticket/491#comment:52](http://www.virtualbox.org/ticket/491#comment:52)

In particular, I did this:

[FONT="Courier New"]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT]

---

### Post by jack frost on 2008-10-07
I will have to give this a try.. I have a 2g phone.... I don't want to keep a windows box just to sync my phone.. I only use the xp vm for some stuff for work and trying to sync the phone..

---

### Post by jack frost on 2008-10-08
> **callmesid said:**
> I was able to get my iPhone to sync. My setup:

Ubuntu 8.04 (Hardy Heron)
[VirtualBox 2.0.2]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")
iPhone 3G (Software version 2.1)

I followed the steps mentioned in the thread on the virtualbox website

[http://www.virtualbox.org/ticket/491#comment:52](http://www.virtualbox.org/ticket/491#comment:52)

In particular, I did this:

[FONT="Courier New"]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT]
that worked.... syncs perfectly with using this post... 
worked with 2g iphone  2.1 firmware , unlocked & jailbroken.. xp vm running in hardy 8.04 amd64

---

### Post by tsbaker on 2008-11-03
Ubuntu 8.10 2.6.27-7 AMD64
iphone 3G FW 2.1 Jail Broken
Virtualbox 2.0.4 PUEL

I used a script from this site after much trial and error following the above instructions. Go to the above referenced site, scroll all the way to the bottom, and check out a post from huanix. use the link to his site and run the script he created. after a reboot my phone synced up just fine. Hopefully this continues to stay working, this is the only reason I still use Windows :)

EDIT:

I can't seem to transfer music manually to my iphone. It syncs, just not manually. Anyone else having this problem. If so, how did you overcome it or have I done something wrong???

---

### Post by kinkdxm on 2008-11-16
THANKS callmesid!!
Worked GREAT!
> **tsbaker said:**
> I can't seem to transfer music manually to my iphone. It syncs, just not manually. Anyone else having this problem. If so, how did you overcome it or have I done something wrong???

[http://www.brighthub.com/mobile/iphone/articles/6129.aspx](http://www.brighthub.com/mobile/iphone/articles/6129.aspx)

---

