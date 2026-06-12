---
title: "fresh install daily live flashplugin-installer failed"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-08-19
any suggestions?
```
sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox xulrunner-1.9 firefox-3.0 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/9,058 B of archives.
After this operation, 188 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 95472 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.3.183.4ubuntu3_amd64.deb) ...
Setting up flashplugin-installer (10.3.183.4ubuntu3) ...
Downloading...
--2011-08-19 16:16:21--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.183.4.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5517014 (5.3M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.3.183.4.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  0%  119K 45s
    50K .......... .......... .......... .......... ..........  1%  351K 30s
   100K .......... .......... .......... .......... ..........  2%  418K 24s
   150K .......... .......... .......... .......... ..........  3%  432K 21s
   200K .......... .......... .......... .......... ..........  4% 1.01M 17s
   250K .......... .......... .......... .......... ..........  5%  721K 16s
   300K .......... .......... .......... .......... ..........  6% 1.37M 14s
   350K .......... .......... .......... .......... ..........  7%  815K 13s
   400K .......... .......... .......... .......... ..........  8% 1.45M 11s
   450K .......... .......... .......... .......... ..........  9% 1.02M 11s
   500K .......... .......... .......... .......... .......... 10% 1.57M 10s
   550K .......... .......... .......... .......... .......... 11% 1.54M 9s
   600K .......... .......... .......... .......... .......... 12% 1.49M 9s
   650K .......... .......... .......... .......... .......... 12% 1.36M 8s
   700K .......... .......... .......... .......... .......... 13% 1.41M 8s
   750K .......... .......... .......... .......... .......... 14% 1.52M 7s
   800K .......... .......... .......... .......... .......... 15% 1.97M 7s
   850K .......... .......... .......... .......... .......... 16% 2.31M 7s
   900K .......... .......... .......... .......... .......... 17% 1.73M 6s
   950K .......... .......... .......... .......... .......... 18% 2.25M 6s
  1000K .......... .......... .......... .......... .......... 19% 1.85M 6s
  1050K .......... .......... .......... .......... .......... 20% 1.99M 6s
  1100K .......... .......... .......... .......... .......... 21% 1.88M 5s
  1150K .......... .......... .......... .......... .......... 22% 2.10M 5s
  1200K .......... .......... .......... .......... .......... 23% 1.74M 5s
  1250K .......... .......... .......... .......... .......... 24% 2.05M 5s
  1300K .......... .......... .......... .......... .......... 25% 1.67M 5s
  1350K .......... .......... .......... .......... .......... 25% 1.98M 5s
  1400K .......... .......... .......... .......... .......... 26% 2.32M 4s
  1450K .......... .......... .......... .......... .......... 27% 1.75M 4s
  1500K .......... .......... .......... .......... .......... 28% 1.31M 4s
  1550K .......... .......... .......... .......... .......... 29% 1.21M 4s
  1600K .......... .......... .......... .......... .......... 30% 1.12M 4s
  1650K .......... .......... .......... .......... .......... 31% 1.07M 4s
  1700K .......... .......... .......... .......... .......... 32% 1.10M 4s
  1750K .......... .......... .......... .......... .......... 33%  902K 4s
  1800K .......... .......... .......... .......... .......... 34% 1.01M 4s
  1850K .......... .......... .......... .......... .......... 35% 1.17M 4s
  1900K .......... .......... .......... .......... .......... 36% 2.31M 4s
  1950K .......... .......... .......... .......... .......... 37% 2.53M 3s
  2000K .......... .......... .......... .......... .......... 38% 2.18M 3s
  2050K .......... .......... .......... .......... .......... 38% 1.88M 3s
  2100K .......... .......... .......... .......... .......... 39% 1.77M 3s
  2150K .......... .......... .......... .......... .......... 40% 1.26M 3s
  2200K .......... .......... .......... .......... .......... 41% 1.59M 3s
  2250K .......... .......... .......... .......... .......... 42% 2.49M 3s
  2300K .......... .......... .......... .......... .......... 43% 2.15M 3s
  2350K .......... .......... .......... .......... .......... 44%  209K 3s
  2400K .......... .......... .......... .......... .......... 45% 6.80M 3s
  2450K .......... .......... .......... .......... .......... 46% 10.7M 3s
  2500K .......... .......... .......... .......... .......... 47% 33.6M 3s
  2550K .......... .......... .......... .......... .......... 48% 32.1M 3s
  2600K .......... .......... .......... .......... .......... 49% 66.0M 3s
  2650K .......... .......... .......... .......... .......... 50% 68.4M 2s
  2700K .......... .......... .......... .......... .......... 51% 64.3M 2s
  2750K .......... .......... .......... .......... .......... 51% 43.4M 2s
  2800K .......... .......... .......... .......... .......... 52% 49.9M 2s
  2850K .......... .......... .......... .......... .......... 53% 41.3M 2s
  2900K .......... .......... .......... .......... .......... 54% 42.4M 2s
  2950K .......... .......... .......... .......... .......... 55% 21.9M 2s
  3000K .......... .......... .......... .......... .......... 56% 60.4M 2s
  3050K .......... .......... .......... .......... .......... 57% 62.9M 2s
  3100K .......... .......... .......... .......... .......... 58% 97.2K 2s
  3150K .......... .......... .......... .......... .......... 59%  134K 2s
  3200K .......... .......... .......... .......... .......... 60%  278K 2s
  3250K .......... .......... .......... .......... .......... 61%  511K 2s
  3300K .......... .......... .......... .......... .......... 62%  587K 2s
  3350K .......... .......... .......... .......... .......... 63%  957K 2s
  3400K .......... .......... .......... .......... .......... 64%  647K 2s
  3450K .......... .......... .......... .......... .......... 64% 2.11M 2s
  3500K .......... .......... .......... .......... .......... 65%  836K 2s
  3550K .......... .......... .......... .......... .......... 66% 1.09M 2s
  3600K .......... .......... .......... .......... .......... 67% 2.25M 2s
  3650K .......... .......... .......... .......... .......... 68% 2.56M 2s
  3700K .......... .......... .......... .......... .......... 69% 1.33M 2s
  3750K .......... .......... .......... .......... .......... 70% 1.22M 2s
  3800K .......... .......... .......... .......... .......... 71% 2.09M 2s
  3850K .......... .......... .......... .......... .......... 72% 2.53M 2s
  3900K .......... .......... .......... .......... .......... 73% 2.31M 2s
  3950K .......... .......... .......... .......... .......... 74% 2.40M 1s
  4000K .......... .......... .......... .......... .......... 75% 2.95M 1s
  4050K .......... .......... .......... .......... .......... 76% 2.66M 1s
  4100K .......... .......... .......... .......... .......... 77% 2.22M 1s
  4150K .......... .......... .......... .......... .......... 77% 2.88M 1s
  4200K .......... .......... .......... .......... .......... 78% 2.75M 1s
  4250K .......... .......... .......... .......... .......... 79% 2.35M 1s
  4300K .......... .......... .......... .......... .......... 80% 1.94M 1s
  4350K .......... .......... .......... .......... .......... 81% 1.58M 1s
  4400K .......... .......... .......... .......... .......... 82% 1.66M 1s
  4450K .......... .......... .......... .......... .......... 83% 1.72M 1s
  4500K .......... .......... .......... .......... .......... 84% 1.60M 1s
  4550K .......... .......... .......... .......... .......... 85% 1.51M 1s
  4600K .......... .......... .......... .......... .......... 86% 2.87M 1s
  4650K .......... .......... .......... .......... .......... 87% 2.53M 1s
  4700K .......... .......... .......... .......... .......... 88% 2.57M 1s
  4750K .......... .......... .......... .......... .......... 89% 6.30M 1s
  4800K .......... .......... .......... .......... .......... 90% 3.86M 1s
  4850K .......... .......... .......... .......... .......... 90% 2.39M 0s
  4900K .......... .......... .......... .......... .......... 91% 1.80M 0s
  4950K .......... .......... .......... .......... .......... 92% 1.64M 0s
  5000K .......... .......... .......... .......... .......... 93% 2.54M 0s
  5050K .......... .......... .......... .......... .......... 94% 2.96M 0s
  5100K .......... .......... .......... .......... .......... 95% 2.80M 0s
  5150K .......... .......... .......... .......... .......... 96% 3.07M 0s
  5200K .......... .......... .......... .......... .......... 97% 3.10M 0s
  5250K .......... .......... .......... .......... .......... 98% 2.73M 0s
  5300K .......... .......... .......... .......... .......... 99% 2.09M 0s
  5350K .......... .......... .......... .......              100% 2.35M=4.8s

2011-08-19 16:16:27 (1.10 MB/s) - `./adobe-flashplugin_10.3.183.4.orig.tar.gz' saved [5517014/5517014]

Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ 

```

---

### Post by cariboo on 2011-08-19
I had the same problem on a fresh install last night, synaptic tried several time to fix it, but eventually I installed the installer from SevenMachines [ppa]("https://launchpad.net/~sevenmachines/+archive/flash").

I assume the problem is with multiarch.

---

### Post by buzzmandt on 2011-08-19
thanks, that worked, but if they're going to not allow 32 bit to work on 64 bit why are they not including flash64 bit in the repos.  why i gotta get ppa for it?  annoying

---

### Post by MadCow108 on 2011-08-19
you probably need to enable multiarch:
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-August/000886.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-August/000886.html)

32bit flashplugin is now installable without ia32-libs :D

---

### Post by cariboo on 2011-08-19
It looks to me from that email, that both the 64 and 32 bit packages will be downloaded if they are available. Why should the 32bit packages be downloaded if I don't need them?

---

### Post by buzzmandt on 2011-08-19
> **cariboo907 said:**
> It looks to me from that email, that both the 64 and 32 bit packages will be downloaded if they are available. Why should the 32bit packages be downloaded if I don't need them?

Well, i tend to agree, buuuutttt, 64bit flash should be available before the 32 bit version is unavailable.  I know it's available in ppa but I don't consider that to count. (although I'm very glad it's there, and thanks for the link to it btw).

---

### Post by MacUntu on 2011-08-20
Hm, so should it be installable with multiarch enabled (because it still fails here after the update and upgrade)?

---

### Post by buzzmandt on 2011-08-20
I think there needs to be a bug against this, anyone know if one is already filed.  If not what we file against.  It's not a bug with flash-installer, it's with the multiarch system.

---

### Post by Bowmore on 2011-08-20
Here's the bug:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/829182](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/829182)

---

### Post by jerrylamos on 2011-08-20
I found a libflashplayer.so from a current Narwhal, copied it to Oneiric home, then:

#! /bin/bash
sudo cp -dpuv libflashplayer.so /usr/lib/mozilla/plugins 

Worked fine.  I don't know for how long before Ubuntu changes something.

Jerry

p.s. a heck of a lot easier than the "install".

---

### Post by buzzmandt on 2011-08-20
> **Bowmore said:**
> Here's the bug:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/829182](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/829182)

thanks, clicked the 'me too' thingy :)

---

