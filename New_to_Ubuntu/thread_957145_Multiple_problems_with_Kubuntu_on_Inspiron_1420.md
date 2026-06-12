---
title: "Multiple problems with Kubuntu on Inspiron 1420"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by WiseMaturin on 2008-10-24
I am somewhat new to Kubuntu, I've had it for two weeks just to test it out, and I've come across a few minor problems.

No sound.
Searched all over the net, tried I don't even *know* how many solutions, and none worked.
I've tried messing with alsa, checking and setting a default sound card, and many other tedious and laborious things.

Wifi problems. This one is hit or miss, and I've never been able to pin down the real problem. Sometimes it won't configure the device, sometimes it doesn't finish retrieving an ip, and most importantly it will not EVER connect to my home wifi system. It's not that it NEVER connects, sometimes it connects extremely quickly. It's just in places that I don't spend hardly any time, and that's great for traveling, but I'd rather be able to connect in my house.

Also, and this one is bizarre... my Vista partition just stopped working one day. GRUB stills shows it there, and I've tried running a diagnostic, but it suggested that perhaps a USB drive was improperly removed, and to restart with it plugged in again.
I've tried every USB item I have, none of them solved it. I've tried all different combinations of USB items, up to 4 at a time even.
When I try to choose Vista from GRUB, it starts to load but never finishes loading Vista. When I try to access the Vista partition while working on Kubuntu, it says 'permissions denied', and doesn't even tell me the size of the partition.
And what may perhaps be a related problem is that when I plug a USB drive into the computer, it pops up normally, but when I try to unmount, it gives an error to the effect "Drive was successfully unmounted, but could not be removed".



I will gladly accept any help for any of the many problems I have encountered, and hope that the details I've given might be of use.
And thank you so much for your time!

---

### Post by WiseMaturin on 2008-10-24
Are these too complicated of problems for this board or something?

Should I be listing this somewhere else maybe?

---

### Post by ardvark71 on 2008-10-24
> **WiseMaturin said:**
> Are these too complicated of problems for this board or something?

Should I be listing this somewhere else maybe?

Well, if nothing else, I can at least try to get things started. :)

First we will need a list of all your devices. Can you post for us a copy of your xorg.conf file? Also, please type this command in a terminal...

```
lspci
```

and post the results.

Best Regards...

---

### Post by igknighted on 2008-10-24
For the sound issue, can you post the results of the command 'aplay -l'?

And also (for both), the results of the command 'lspci'?

Finally (just a little forum etiquette tip), this time of day tends to be slower on the forums.  Many times you get responses in minutes here, but often it takes hours.  Please wait 24 hours before bumping your own thread.

---

### Post by WiseMaturin on 2008-10-24
Sorry about not replying sooner. I lost power last night, and had some stuff to take care of at my college this morning.
After my workout and breakfast, I'll post the result of ```
lspci
``` and ```
aplay -l
```.

Thanks for all your help guys, and for the tip on etiquette as well.

---

### Post by WiseMaturin on 2008-10-24
Alright, here is my result for lspci.

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control
ler #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (r
ev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (r
ev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll                   er #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control                   ler #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller                    (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Contro                   ller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC                   I Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapte                   r (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (re                   v 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet                    PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Networ                   k Connection (rev 61)
```



And my result for aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```



Looking forward to trying out some work-arounds, if you've got any. :)

---

### Post by ardvark71 on 2008-10-25
Hi...

Please excuse me if I may have missed it somewhere but are you running Kubuntu 8.04?

Best Regards...

---

### Post by WiseMaturin on 2008-10-25
> **ardvark71 said:**
> Hi...

Please excuse me if I may have missed it somewhere but are you running Kubuntu 8.04?

Best Regards...

You missed nothing, I just completely forgot to specify which version I am running. lol
And you are correct sir, I am on 8.04. :)

---

### Post by ardvark71 on 2008-10-25
Hi...

As to the sound issue, you may have already seen this page but it does give a clue as to what's going on, apparantly the kernel is missing a module, at least for the x64 version...

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559)

Although most of the page deals with earlier versions of Ubuntu/Kubuntu, there may be a workaround or fix that may help.

With the wireless problem, here is a thread that may help...

[http://ubuntuforums.org/showthread.php?t=950345](http://ubuntuforums.org/showthread.php?t=950345)

Hope this helps at least a little bit... ;)

Best Regards...

---

### Post by WiseMaturin on 2008-10-29
> **ardvark71 said:**
> Hi...

As to the sound issue, you may have already seen this page but it does give a clue as to what's going on, apparantly the kernel is missing a module, at least for the x64 version...

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559)

Although most of the page deals with earlier versions of Ubuntu/Kubuntu, there may be a workaround or fix that may help.

With the wireless problem, here is a thread that may help...

[http://ubuntuforums.org/showthread.php?t=950345](http://ubuntuforums.org/showthread.php?t=950345)

Hope this helps at least a little bit... ;)

Best Regards...

I am going to try and upgrade to Intrepid, and see how many of my problems that will solve. I'll nab the linux-backports-modules-intrepid and see if that clears up my wireless problem, and once that's done I'll take a stab at the sound malfunction.
Thanks are in order very soon, I believe. :)

---

### Post by WiseMaturin on 2008-10-29
I am now on Intrepid.

Still no sound though. Apparently alsa only has drivers for up to ICH7, and I have ICH8. So I don't really know what to do on that one. >_>



EDIT: Fixed some of the page-loading problems I had before.
And the connectivity problem is gone as well with the upgrade to the linux-backports-module-intrepid. =D

---

### Post by WiseMaturin on 2008-11-13
Sound kind of works now, but is BARELY audible at the highest volume settings. I know I've seen many pages of people asking this one, but I've seen sooo many pages of all kinds of problems I can't remember the solution to this one. lol

Any help?

Btw, my computer is apparently running a sound card in the ICH8 family, and Alsa only supports up to ICH7.
Dunno if that'll help at all, but thank you once again. :D

---

