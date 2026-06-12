---
title: "Need a lightweight distro with Atheros supported"
date: 2007-07-17
forum: Other OS Talk
---

### Post by quadomatic on 2007-07-17
I need a lightweight distro for an old laptop that has a 600 mhz Pentium III and 256 MB of ram.

The big problem, is that I want support for the atheros wireless chipset out of the box, because I can't get internet on it otherwise. I tried Wolfix and Zenwalk, and those don't seem to work. Arch Linux doesn't seem to have it either.

Does anyone have any other suggestions?

I'm in the middle of getting Puppy Linux, which I've heard good things about. I also saw that the atheros drivers are included.

---

### Post by johnny4north on 2007-07-18
i believe puppylinux is a great distro - here is a link to puppylinux forum on atheros - [http://www.murga-linux.com/puppy/viewtopic.php?t=8488](http://www.murga-linux.com/puppy/viewtopic.php?t=8488)
here is link to madwifi for other distros - [http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)
i would suggest trying DSL - [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)   Good luck:)

---

### Post by quadomatic on 2007-07-18
> **johnny4north said:**
> i believe puppylinux is a great distro - here is a link to puppylinux forum on atheros - [http://www.murga-linux.com/puppy/viewtopic.php?t=8488](http://www.murga-linux.com/puppy/viewtopic.php?t=8488)
here is link to madwifi for other distros - [http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)
i would suggest trying DSL - [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)   Good luck:)

I tried Puppy Linux, and I thought it was REALLY good, and it had atheros support. I tried a frugal install, but I couldn't get it to boot afterwards! Maybe I installed GRUB wrong or something...Was I supposed to choose MBR or something else?

---

### Post by xpod on 2007-07-18
How about Tinyme??

[http://ubuntuforums.org/showthread.php?t=502559](http://ubuntuforums.org/showthread.php?t=502559)
[http://tinyme.mypclinuxos.com/](http://tinyme.mypclinuxos.com/)

I cant tell you if it`ll work out the box with your wireless i`m afaid so you`d need to look into that.
It`s not as quick as puppy from my very limited experience so far but it`s a neat,simple little distro.....thanks to RAV TUX for pointing it out of course:)

Puppy`s grub can be a bit confusing(as can tinyme`s) but if you just install to MBR it should be fine.If it fails to pick up any other operating systems then their easy enough to add.

You dont actually even need to install puppy as you can quite simply just save your session when shutting down the cd.I do prefer to install myself though.

EDIT: you could actually run Ubuntu reasonably well on that i reckon.Or even better would be xubuntu.
I dont think you *need* to go soo lightweight but of course thats down to you.

---

### Post by igknighted on 2007-07-18
SAM Linux would be an excellent choice on that.  Check out the link in my sig.

---

### Post by ThinkBuntu on 2007-07-18
dyne:bolic is great for the lowest of low-end computers but is the best multimedia distro out there. Of course, it includes Abiword, Firefox, Thunderbird, etc. so you won't be limping, and it uses Xfce (no bizarre, hideous desktop environments!). My copy has the ath_pci and ath_hal modules, which are the open source drivers for Atheros cards, courtesy of Madwifi. I'll be honest: the Live CD failed to activate my wireless. But you may have better luck, especially if you install the system.

---

### Post by jrusso2 on 2007-07-18
> **igknighted said:**
> SAM Linux would be an excellent choice on that.  Check out the link in my sig.

I second sam linux, its a complete distro and I have it running on a laptop with atheros card and its only 128 mb of ram and 400 mhz.

---

### Post by igknighted on 2007-07-18
> **ThinkBuntu said:**
> dyne:bolic is great for the lowest of low-end computers but is the best multimedia distro out there. Of course, it includes Abiword, Firefox, Thunderbird, etc. so you won't be limping, and it uses Xfce (no bizarre, hideous desktop environments!). My copy has the ath_pci and ath_hal modules, which are the open source drivers for Atheros cards, courtesy of Madwifi. I'll be honest: the Live CD failed to activate my wireless. But you may have better luck, especially if you install the system.

I've seen this several times.  Linux Mint for example refuses to recognize my atheros wifi, but once installed it works perfectly.  Perhaps dyne:bolic is the same way.

---

### Post by Rumor on 2007-07-18
> **quadomatic said:**
> I need a lightweight distro for an old laptop that has a 600 mhz Pentium III and 256 MB of ram.

The big problem, is that I want support for the atheros wireless chipset out of the box, because I can't get internet on it otherwise. I tried Wolfix and Zenwalk, and those don't seem to work. Arch Linux doesn't seem to have it either.


Arch has it, but not on the install disc. Perhaps you could download the package separately and install it from a CD? pacman -A  /path/to/pkg.tar.gz

```
 testing/madwifi 0.9.3.1-5
    Madwifi drivers for Atheros wireless chipsets. For stock arch 2.6 kernel
testing/madwifi-utils 0.9.3.1-4
    Userspace tools of madwifi drivers for Atheros wireless chipsets.
extra/madwifi 0.9.3.1-1
    Madwifi drivers for Atheros wireless chipsets. For stock arch 2.6 kernel
extra/madwifi-ck 0.9.3.1-1
    Madwifi drivers for Atheros wireless chipsets. For kernel26ck.
extra/madwifi-suspend2 0.9.3.1-1
    Madwifi drivers for Atheros wireless chipsets. For kernel26suspend2
extra/madwifi-utils 0.9.3.1-1
    Userspace tools of madwifi drivers for Atheros wireless chipsets.
```

---

### Post by quadomatic on 2007-07-18
SAM Linux looks like a complete OS, and it seems like it will run fast. I just burned it now, so I'm going to go try it out.

---

### Post by quadomatic on 2007-07-18
I got SAM working, but the sound is screwed up. I can't raise the volume, because if I do, I get a really loud, high-pitched "eeeeeeeeeeeee" noise.

Anyone know what might be causing that?

I'm using the "ymfpci" driver

---

### Post by igknighted on 2007-07-18
> **quadomatic said:**
> I got SAM working, but the sound is screwed up. I can't raise the volume, because if I do, I get a really loud, high-pitched "eeeeeeeeeeeee" noise.

Anyone know what might be causing that?

I'm using the "ymfpci" driver

Is your microphone on and enabled?  Could you be getting feedback?  Try muting the microphone in alsamixer.  Then see if that helped.  If that doesn't work, run the program "alsaconf" as root on the cli.  Accept the defaults.  Test again to see if the sound is fixed.

---

### Post by dca on 2007-07-19
Howza' bout Xubuntu?

---

