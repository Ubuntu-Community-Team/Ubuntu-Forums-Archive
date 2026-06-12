---
title: "Sony Ericsson K750i as usb mass storage"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by teranex on 2008-11-17
Hi,

I recently installed Ubuntu 8.10 (using Wubi) and i have a problem with my Sony Ericsson K750i. When I connect the phone to my computer (using the usb cable that came with the phone), ubuntu detects it and ask to configure it.
Also in Nautilus an icon ("MemoryStick Drive") appears. However, when i double click on this icon, it gives me an error: "can't mount file". When i first remove the MemoryStick Pro Duo card from my phone before connecting it, it gives me the error "No media in drive" (or something similar), when i try to mount it (that sounds logical). But when i insert the MemoryStick and retry to mount it, it keeps saying that there is no media in the drive.
On Windows XP/Vista it works without any problems. When i connect the phone the computer sees it as a mass storage device and i can open it in explorer.

---

### Post by kestrel1 on 2008-11-17
I have the same phone, but have been unable to get it to work under Ubuntu or any other Linux distro that I have tried. I think it is down to the drivers. As you say, it works fine under Win XP, but this is only after installing the drivers from the CD. I can't see any way around this at present.

---

### Post by teranex on 2008-11-17
> **kestrel1 said:**
> I have the same phone, but have been unable to get it to work under Ubuntu or any other Linux distro that I have tried. I think it is down to the drivers. As you say, it works fine under Win XP, but this is only after installing the drivers from the CD. I can't see any way around this at present.

hmmm after yahoo-ing a bit on "k750i linux", i found various "success stories" about using the k750i under Linux, so i guess it really is a problem with our setup...

[http://stefans.datenbruch.de/k750i/#usbcable](http://stefans.datenbruch.de/k750i/#usbcable)
[http://contented.life.eu.org/articles/sony-ericsson-k750i-and-linux/](http://contented.life.eu.org/articles/sony-ericsson-k750i-and-linux/)
[http://www.esato.com/board/viewtopic.php?topic=93070](http://www.esato.com/board/viewtopic.php?topic=93070)

If only i knew how to fix it...

---

### Post by philinux on 2008-11-17
Is your os 8.04 or 8.10?

---

### Post by teranex on 2008-11-17
> **philinux said:**
> Is your os 8.04 or 8.10?

8.10 (installed with Wubi on a NTFS partition)

---

### Post by philinux on 2008-11-17
My K810i mounts ok after choosing file transfer mode.

---

### Post by teranex on 2008-11-17
> **philinux said:**
> My K810i mounts ok after choosing file transfer mode.

Where do you choose the mode of your phone? I have never come accross any such option on the k750i. When i connect the phone on Windows it recognizes it both as a phone [I]and[ /I] as a mass storage device and i can do both phone operations (syncing contacts etc) and browse the files on the memory card.

---

### Post by kestrel1 on 2008-11-17
I will give mine another go on my laptop that is running 8.10. My Desktop (at home) is running 8.04 at present. It could be something to do with the way you have Ubuntu installed. I have never tried the wubi install, If I run it through Windows I use a virtual machine, but I much prefer a clean install on a normal system. Have you tried booting your system with the live CD & seeing if it will mount correctly then?

---

### Post by kestrel1 on 2008-11-17
Just plugged the phone in via the usb cable & it was recognised & I can get access to everything on the memory card. The only thing you can't do is get to anything on the internel phone memory. I am suspecting the wubi type installation is causing your problems. Try booting from the live CD as I suggested above.

---

### Post by philinux on 2008-11-17
I've a feeling it's 8.10 as it has fixed a bug where my canon camera was not mounted as a usb mass storage device. Had to get a card reader for 8.04. Only £4 though.

---

### Post by teranex on 2008-11-17
> **kestrel1 said:**
> Just plugged the phone in via the usb cable & it was recognised & I can get access to everything on the memory card. The only thing you can't do is get to anything on the internel phone memory. I am suspecting the wubi type installation is causing your problems. Try booting from the live CD as I suggested above.

Hi,

I just booted from the live CD but it gives the exact same result. The reason i installed with Wubi is because i wanted to give Ubuntu a quick try, to see if everything that i need and use works. Until now i just have a few issues left (of which my phone is one :) ), so i'll probably go for a single boot with Ubuntu in a few weeks. So maybe a regular ubuntu will fix this... :)
If it doesn't fix it, i'll probably have to buy a seperate cardreader.

thx for the help!

---

### Post by philinux on 2008-11-17
Wubi will work exactly the same as a "proper" install. It's more likely then that your phone and linux dont get on that well. My 810i show as a phone and phonecard on the desktop. Full access to phone internals.

---

### Post by teranex on 2008-11-18
I got it working :) !!

When i use the commandline to mount my Phone it works:

```

sudo mkdir /media/k750i
sudo mount -t vfat /dev/sdc1 /media/k750i -o uid=1000,gid=100,utf8,dmask=027,fmask=137

```

After i mount it, there also appears on icon on the desktop "4.1 GB Media". In Nautilus (computer:///), i see 2 icons: the "MemoryStick Drive" and "4.1 GB Media"...

---

### Post by kestrel1 on 2008-11-18
Cool.
Have you got a 4GB card in the phone?
I am wondering, because I have seen reports that it will only take a 1GB, so haven't bothered to upgrade it yet, but if you have a 4GB working then I might get myself a 4GB card.

---

### Post by teranex on 2008-11-18
> **kestrel1 said:**
> Cool.
Have you got a 4GB card in the phone?
I am wondering, because I have seen reports that it will only take a 1GB, so haven't bothered to upgrade it yet, but if you have a 4GB working then I might get myself a 4GB card.

Jup, 4GB works. But according to what i read that is the biggest card it can read. I think i found that info on the Esato forums ([http://www.esato.com/](http://www.esato.com/)). According to the Sony Ericsson site the biggest card it supports is 2GB: [http://www.sonyericsson.com/memorystick/](http://www.sonyericsson.com/memorystick/)

---

### Post by kestrel1 on 2008-11-18
Thanks for the info. I will look in to getting myself a 4GB card now.
Cheers

---

