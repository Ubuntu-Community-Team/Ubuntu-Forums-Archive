---
title: "instalation freezes"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by pedrotuga on 2008-08-04
This has been a headache, I am trying to install ubuntu on an old laptop of mine but the installation freezes when the files are being copyed.

I used this very CDto install ubuntu on other machine and it worked, i've checked the CD for errors, no errors.

Both the CD driver and the HD are working properly, the CD works perfectly as a liveCD, i've formated the hard drive a couple of times ans stored files in it, no problem at all, apparently everything is working fine, but the damn installation doesn't work.

This motherboard doesn't support usb boot, otherwise i would be fine. Is it possible to boot using a liveCD and install from yet another location, like a usb stick or so?
I wouldn't mind trying other distro if it would be convenient in some way in this case.

---

### Post by northern lights on 2008-08-04
Check out [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") - I'd prefer the NetInstall, but you can also load an .iso.

Also, how old is your laptop, i.e. some specs?

---

### Post by snowpine on 2008-08-04
How long does it freeze for? Depending on the vintage of the computer, I've had installations appear to freeze for hours... try leaving it running overnight and see if it works. :-)

+1 to Northern Lights, specs for your computer would be helpful.

---

### Post by Troll_the_Great on 2008-08-04
To install with the live CD you need at least 384 MB RAM.If your computer doesn't have the minimum RAM requirements try installing using the alternate CD.
Cheers!

---

### Post by pedrotuga on 2008-08-04
it's five years old, it's an Acer Aspire 1310, it came with 256MB of RAM but i already added 256 more so now it has 512.

I would give a try in letting it installing over the night, but i seriously doubt it will work, the hard drive and processor led indicators are do not lite and the cd drive is also stoped. Also the mouse pointer doesn't move.

BTW.. where can i check the specs of my system, like, i vagely suspect the RAM is broken.

---

### Post by halitech on 2008-08-04
if you suspect a ram problem, when you bot there should be an option to run memtest, it will test your memory to ensure there are no problems with it. Let it run for at least a few hours

---

### Post by northern lights on 2008-08-04
> **pedrotuga said:**
> BTW.. where can i check the specs of my systemIf it's booting from the LiveCD, run```
sudo lshw
```from any shell prompt.

> **pedrotuga said:**
> i vagely suspect the RAM is broken.Run```
free -m
```

---

### Post by pedrotuga on 2008-08-04
lshw outputs this... it appears that everything is ok, 256+224, I wonder why 224 instead of 256 though.

```
 *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM DRAM EDO
             physical id: 0
             slot: DRAM Slot 0
             size: 256MiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          physical id: 2
        *-bank UNCLAIMED
             description: DIMM DRAM EDO
             physical id: 0
             slot: DRAM Slot 1
             size: 224MiB
             width: 64 bits
     *-memory:2 UNCLAIMED
          physical id: 3
        *-bank UNCLAIMED
             description: DIMM DRAM EDO [empty]
             physical id: 0
             slot: DRAM Slot 2
             width: 64 bits
     *-memory:3 UNCLAIMED
          physical id: 6
     *-memory:4 UNCLAIMED
          physical id: 7

```

---

### Post by halitech on 2008-08-05
with it being a laptop it may be using shared memory for the video card instead of dedicated ram for the video so that could be why it's showing 12 meg less.

---

### Post by snowpine on 2008-08-05
The Alternate Install CD sometimes works where the Live CD fails, for a variety of reasons, perhaps that's worth a try?

Another option is a minimal command-line installation, then 'sudo apt-get install ubuntu-desktop' to install by downloading. And then of course there is always Xubuntu.

---

### Post by pedrotuga on 2008-08-05
> **halitech said:**
> with it being a laptop it may be using shared memory for the video card instead of dedicated ram for the video so that could be why it's showing 12 meg less.
Makes sense. And that's the case, this computer has shared memory.

> The Alternate Install CD sometimes works where the Live CD fails, for a variety of reasons, perhaps that's worth a try?

Another option is a minimal command-line installation, then 'sudo apt-get install ubuntu-desktop' to install by downloading. And then of course there is always Xubuntu.
Thanks for the tips. Problem is nowadays the ubuntu iso for a server installation has to be downloaded separately.
I don't have the possibility to burn cds whenever I want at this time, so i think I will just use puppy linux which I already used before and was quite impressed with.
Or maybe i take the chance to guive a try to wolvix.

Either way, thank you guys.

---

### Post by northern lights on 2008-08-05
> **northern lights said:**
> Check out [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") - I'd prefer the NetInstall, but you can also load an .iso.If you can't burn CDs all the time this is the the ultimate solution.

With this app you can initiate the installation of Ubuntu, Ubuntu Server, Kubuntu, Xubuntu, Edubuntu, Gentoo, Mint, Debian and a few more on the next reboot. Either from an .iso or in the case of Ubuntu also directly from the net. You can also load an .iso on a USB flashdrive and install from there.
Unetbootin offers binaries for Linux, Windows and Macs.
This little thingy is mighty powerful.

---

