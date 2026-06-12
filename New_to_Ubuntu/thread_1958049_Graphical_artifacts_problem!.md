---
title: "Graphical artifacts problem!"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by DisappearingOak on 2012-04-13
Hi, I have a Radeon HD 4250 onboard graphic device, and Windows and Ubuntu/Unity runs fine on it. But in Kubuntu, everything works mostly fine but in some applications like libreOffice, maximizing the window results in lots of artifacts for a few seconds. This also happens when fullscreening facebook games. How can I solve this? I'm on the default drivers which work fine for me except for this tiny problem. I tried using the fglrx drivers once to see if that solves the problem, but actually it made everything visible on the monitor corrupted and every window and panel started having artifacts. So I uninstalled it and returned to the default drivers. I just wish this small problem was solved to make my kubuntu experience pleasing and complete.

Thanks for your help.

---

### Post by Zorael on 2012-04-14
It's not a *good* solution, but you could try adding the _unsupported_ [xorg-edgers PPA](https://launchpad.net/~xorg-edgers/+archive/ppa). You'd get very fresh and continually updated videocard and input drivers, as well as new versions of X.org. No guarantees it will make things better, mind. (It's always a good idea to have a live usb around!)

In Muon (the package manager): *Settings* -> *Configure Software Sources*. It will ask for your password. In the Other Software tab, hit *Add* and enter '**ppa:xorg-edgers/ppa**' in the dialogue window that pops up.

Then Close everything to get back to Muon, and let it upgrade packages. Restart your machine for everything to take effect. (Or restart X if you know how to do that.)

Alternatively, in a terminal;
```
$ sudo add-apt-repository ppa:xorg-edgers
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

---

### Post by QIII on 2012-04-14
What version of Ubuntu?

When you installed the ATI driver, did you do

```
sudo aticonfig --initial -f
```

before restarting?

How old is the board physically?  Has the integrated chip ever overheated?   Artifacts with both the open source and proprietary drivers is of some concern.

Ditch Muon.  It's an abortion right now, unfortunately.  One hopes it will get better soon.  Install Synaptic.

---

### Post by DisappearingOak on 2012-04-16
> **Zorael said:**
> It's not a *good* solution, but you could try adding the _unsupported_ [xorg-edgers PPA](https://launchpad.net/~xorg-edgers/+archive/ppa). You'd get very fresh and continually updated videocard and input drivers, as well as new versions of X.org. No guarantees it will make things better, mind. (It's always a good idea to have a live usb around!)

In Muon (the package manager): *Settings* -> *Configure Software Sources*. It will ask for your password. In the Other Software tab, hit *Add* and enter '**ppa:xorg-edgers/ppa**' in the dialogue window that pops up.

Then Close everything to get back to Muon, and let it upgrade packages. Restart your machine for everything to take effect. (Or restart X if you know how to do that.)

Alternatively, in a terminal;
```
$ sudo add-apt-repository ppa:xorg-edgers
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

I did as you suggested and now, with the updated drivers, the problem seems to have gone in some places like resizing libreoffice windows. That works fine now. But I did experience new problems in some places, for instance, the plymouth splash on startup has a little tearing effect towards the end and when playing flash games on facebook, there are rectangular video glitches (some box like lines appear when playing). My motherboard is only two months old. So I think it's a driver problem. I wonder where to file bug reports for the driver and which logs I need to put up.

Ubuntu version is oneiric ocelot, and now updated with the xorg-edgers ppa (to the poster above)

---

### Post by Zorael on 2012-04-16
If plymouth is affected that sounds like it came with a kernel upgrade. Looking at the contents of the ppa it has the 3.2.0-23.36 kernel available for oneiric, likely backported from precise.

As for the flash image corruption, I haven't the slightest idea. Have you tried disabling video acceleration?

[img]http://i.imgur.com/M6DFF.jpg[/img]

---

### Post by DisappearingOak on 2012-04-16
> **Zorael said:**
> If plymouth is affected that sounds like it came with a kernel upgrade. Looking at the contents of the ppa it has the 3.2.0-23.36 kernel available for oneiric, likely backported from precise.

As for the flash image corruption, I haven't the slightest idea. Have you tried disabling video acceleration?

[img]http://i.imgur.com/M6DFF.jpg[/img]

Hi, I retried installing fglrx again, and except for the plymouth splash being a little blurry (seems like it's running at lower resolution), everything is running smoothly now. Thanks for your help.

---

