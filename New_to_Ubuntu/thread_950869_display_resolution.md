---
title: "display resolution"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by bobnic6 on 2008-10-17
Hi all,

trying Ubuntu in VirtualBox.

The only screnn resolutions available are 800x600 & 640x480 which are VERY small.

Is it possible to get 1280x1024 or better?
if so, how?

TIA

Bob

---

### Post by SpenceMakesSense on 2008-10-17
try installing guest additions

---

### Post by SunnyRabbiera on 2008-10-17
> **bobnic6 said:**
> Hi all,

trying Ubuntu in VirtualBox.

The only screnn resolutions available are 800x600 & 640x480 which are VERY small.

Is it possible to get 1280x1024 or better?
if so, how?

TIA

Bob

If you giving Ibex a test run in a VM then this is a known issue.

---

### Post by HittingSmoke on 2008-10-17
> **bobnic6 said:**
> Hi all,

trying Ubuntu in VirtualBox.

The only screnn resolutions available are 800x600 & 640x480 which are VERY small.

Is it possible to get 1280x1024 or better?
if so, how?

TIA

Bob

I don't know about running in VM as I've never tried it, but I have this problem on fresh installs when I try to enable restricted video drivers via apt-get or the Drivers Manager. I have to use EnvyNG to download restricted drivers for them to install properly and get my resolution over 800x600.

If you're running an Nvidia or ATI video card its worth a try, just grab EnvyNG from Synaptic and run it, it should be pretty self explanatory.

---

### Post by bobnic6 on 2008-10-18
> **SpenceMakesSense said:**
> try installing guest additions

OK, I can see the file for that BUT I can't get it to run. I presume that double clicking it does not work in Linux?

Cheers

Bob

---

### Post by bobnic6 on 2008-10-18
> **SunnyRabbiera said:**
> If you giving Ibex a test run in a VM then this is a known issue.

Hi

what is Ibex?

Cheers

Bob

---

