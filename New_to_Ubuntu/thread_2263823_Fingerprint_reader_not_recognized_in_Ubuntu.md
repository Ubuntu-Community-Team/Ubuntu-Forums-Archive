---
title: "Fingerprint reader not recognized in Ubuntu"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by anbu-s on 2015-02-03
I've a Dell E6430 with fingerprint reader. Cannot get this to work in gnome ubuntu. Installed the fingerprint gui, but it says no fingerprint devices found. As you can see in this screenshot, the fingerprint device is listed in the list of devices.

How can i get this to work? Please help

---

### Post by anbu-s on 2015-06-25
Any update on this?

---

### Post by yetimon_64 on 2015-06-25
What is the device ID of the fingerprint reader? To find it use the "lsusb" command in terminal (without the quotes). 

As an example of an unsupported device in either Ubuntu or the fingerprint-gui ppa, my fingerprint reader's ID is shown highlighted in the next quote box...
> Bus 001 Device 003: ID **138a:0050** Validity Sensors, Inc.

I did a search on google for that device ID and Ubuntu 14.04. By doing this I managed to find a video of it in action and a fork of libfprint by the developer that posted the video. The developer has a written a driver for my particular device hosted on Github in the libfprint fork he maintains.

I built libfprint which includes the device driver from the Github source code. I normally wouldn't suggest a beginner build from source but did read somewhere related to the ppa that "if your device is not supported already in the ppa, don't expect it to ever be as development of new device drivers in this area is extremely low " or wording to that effect. 

The device now works, though not 100% stable. The fprint daemon crashes regularly on login and the verification only works about 40 to 50 % of the time, but at least it is usable (for me). Even for an "advanced beginner to intermediate level" user like myself, building that library and driver and getting the system working with it was extremely difficult. It took me the better part of a full day to get it all running.

IF, you have the same device number all I can do to help is point you to the Github source and the developers video. NO step by step instructions are supplied anywhere that I could find, you would need to be one very brave/fearless beginner to even think of attempting to build such a library/driver AND be able to get the system to use it. 

I would not even know how to start advising you if you were to attempt such, as I kept NO notes on how it was done. I would describe my mindset while doing this an "autopilot" or "deep-hack" mode one. A bit like a "turn off all fear and be prepared for a rebuild if things go awry" mode ... end result for me was a working fingerprint reader, but it was a very complex route I took to have it work in the end.

IF your device is the same number as mine I will post the links to the Github source and the developers video but can't advise much past there I'm afraid. I would not have the confidence to walk a beginner through what for me was and extremely messy procedure, I'd be afraid of possibly leaving you with a compromised machine as authentication is a pretty important aspect of system security etc.

Cheers, yeti.

---

### Post by Vladlenin5000 on 2015-06-26
The list of supported devices is in the project's Launchpad page: [https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)
The most common from 10 years ago or so should all be supported. Do not expect support OOTB for any newer device.

---

