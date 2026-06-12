---
title: "VIA tech graphics card driver problem"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by malkmus on 2008-10-20
hello everyone,
new to linux here. i installed the system without any problems today. but evrything except the graphics card seems to work fine. my network card and audio have no problems whatsoever (both are from VIA). i tried to install the driver from their website but i couldnt do it.

here's my lspci report form the terminal


```
 
0:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
(rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:01.0 Aud
```


can anyone help me out? i looked around on the net but i had to change some grub settings and all. i am just not that familiar with linux yet. a nice little tutorial from any of the gurus will help me out of this jam.

sorry, i know this problem must have come up now and then before but i just couldnt help myself from joining this forum. you guys have a nice little community.


thanks in advance.

m

---

### Post by roger_1960 on 2008-10-20
Hi

I have had problems with VIA drivers as well.  In my case Unichrome S3.  The [www.viaarena.com](www.viaarena.com) site appears to have drivers for Ubuntu 7.04 but not for later versions.  The one they have definitely does not work with Hardy.  I have looked for a long time but cannot find a solution to this and so have to live without 3D accel on the machine afflicted with this chipset!

---

### Post by malkmus on 2008-10-20
Thanks for the reply. So basically I have to use ubuntu hardy without a graphics driver for VIA. That kind of sucks.


Anyone else have a workaround to this problem?


Thanks.

m

---

### Post by starcannon on 2008-10-20
I screwed up and bought an Everex Cloudbook with a VIA chipset on it (knowing that VIA has never been linux friendly). I assumed because it shipped with linux that the manufacture had sorted it out; I was wrong. Moral to the story, try not to give VIA money, their Linux support is scant at best. If your able to install a different video card (even a cheap one) an Nvidia is your best option.

GL and "replace the VIA card" is sadly the best advice I have.

---

### Post by epidemiks on 2008-10-20
> Chrome9 HC IGP

if memory serves me, my girlfriend's pioneer laptop uses the same integrated graphics. 
I gave up on it late last year. Gutsy worked ok with vesa, but I couldn't get it to even boot with Hardy.

---

### Post by malkmus on 2008-10-21
I looked at the linux support forum for the via tech. They said to install the graphics driver from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

I downloaded the file for ubuntu 8.04 lts and platform (cn896+vt8251). I assume that that's my platform, but I could be very well wrong.

While trying to install the driver file I get this message in the terminal.


```
install the via driver!
...mv: cannot move `/usr/lib/xorg/modules/drivers/via_drv.so' to `/usr/lib/xorg/modules/drivers/via_drv.so.viabak': Permission denied
cp: cannot remove `/usr/lib/xorg/modules/drivers/via_drv.so': Permission denied
...mv: cannot move `/lib/modules/2.6.24-19-generic/kernel/drivers/char/agp/via-agp.ko' to `/lib/modules/2.6.24-19-generic/kernel/drivers/char/agp/via-agp.ko.viabak': Permission denied
cp: cannot remove `/lib/modules/2.6.24-19-generic/kernel/drivers/char/agp/via-agp.ko': Permission denied
...cp: cannot create regular file `/usr/lib/libGL.so.1.2.via_chrome9': Permission denied
ln: cannot remove `/usr/lib/libGL.so': Permission denied
ln: cannot remove `/usr/lib/libGL.so.1': Permission denied
cp: cannot create regular file `/usr/lib/dri/via_chrome9_dri.so': Permission denied
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
...cp: cannot create regular file `/lib/modules/2.6.24-19-generic/kernel/drivers/char/drm/via_chrome9.ko': P


Permission denied

```



Has anyone come across this? I might be doing something wrong. Any kind of help would be appreciated.


Thanks a ton.


m

---

### Post by starcannon on 2008-10-21
you must run the driver you downloaded as super user:
```
sudo some_file_name.run_or_bin
```

---

### Post by malkmus on 2008-10-21
ok so i managed to install it from terminal. now the whole system is screwed. when loading ubuntu the whole screen goes blank. anyway, to uninstall this driver? i'd rather go back to the crappy colors on the monitor rather than nothing at all.


aaah!!! damn you via tech!!!!!!

---

### Post by stalkingwolf on 2008-10-21
For those with the S3 unichrome pro card You might try Ubuntu EEE 8.04.1.
I have had mixed success with it and this card.  It works great on my EEEPC
and on my desktop with this adapter, but not on my everex stepnote.

For the everex I have a custom 7.04 cd that I made from a Toshiba Tecra
that the graphics work from the live cd (havent installed yet).

---

### Post by starcannon on 2008-10-21
Anyway you can share that custom 7.04 disk? I have an everex cloudbook that i'd be willing to give another run at, after much gnashing of teeth I finally put something else on it. Would prefere buntu though.

---

### Post by Vaphell on 2008-10-26
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

there is a driver for Ubuntu 8.04

my GF's laptop has P4M900 and I managed to make it work, compiz  and stuff - in my case beta version, it worked and I haven't touched it since, it's god damn fragile

There are some caveats though:
- it seems to be working ONLY with kernel 2.6.24-16, any upgrade causes X crashes, you are apparently using -19 version - walkaround: edit /boot/grub/menu.lst and set 2.6.24-16 as default, don't bother trying newer versions if you manage to get 3d working
- possible manual tweaking of xorg.conf and whitelisting 'via' in compiz config required

more info:
[http://www.tkarena.com/forums/linux-arena/37115-new-drivers-today-linux-via-com-tw.html](http://www.tkarena.com/forums/linux-arena/37115-new-drivers-today-linux-via-com-tw.html)

you say you don't have any problem with sound... are you sure your headphone jack is working and muting speakers while in use? I had to get alsa sources and manually patch one file, compile and then install to get it work

EDIT: I see that on that download page there is some kernel patch so it should be possible to tweak kernel to use gfx driver with no problems... i have also read that reportedly -21 doesn't require patching anymore, but i can't say if it's true.

---

