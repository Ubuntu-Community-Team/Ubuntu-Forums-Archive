---
title: "The latest stable nvidia-current 275.19 is here (deb)"
date: 2011-07-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-21
For those of you interested in deb packaged latest stable nvidia-current (275.19);
you can download it from X Updates (Ubuntu X).

Update:
The Oneiric build has been removed from the PPA.

---

### Post by Harry33 on 2011-07-21
The latest nvidia-current beta driver (280.04) is about to be built in Xorg-edgers PPA.

>   * New upstream release
    - Incremental bug fixes.
    - Preliminary support for X.Org xserver ABI 11, used in xserver 1.11 RC 1.
 -- Rico Tzschichholz <email address hidden>   Thu, 21 Jul 2011 13:09:28 +0200

---

### Post by caryb on 2011-07-21
Unfortunately I cant install any Nvidia prop driver as I get this...

root@stinkpad:# apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x11-common : Depends: xdiagnose but it is not going to be installed
E: Broken packages

Anyone else with this problem? BTW am on Kubuntu 64 bit current

Cary

---

### Post by Harry33 on 2011-07-22
> **caryb said:**
> Unfortunately I cant install any Nvidia prop driver as I get this...

root@stinkpad:# apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x11-common : Depends: xdiagnose but it is not going to be installed
E: Broken packages

Anyone else with this problem? BTW am on Kubuntu 64 bit current

Cary

The newest, fixed x11-common package (7.6+7ubuntu5) does not anymore depend on xdiagnose. It is in the repos now.

---

### Post by VinDSL on 2011-07-22
Interesting!

Updated already...  :D

> 
nvidia-graphics-drivers (**[COLOR="Red"]275.21-0ubuntu1~oneiric~xup1[/COLOR]**) oneiric; urgency=low

  * Restored the release splash screen in the NVIDIA X driver (the beta splash
    screen was accidentally reenabled between 275.09.07 and 275.19).
  * Fixed a bug that caused nvidia-settings to crash when configuring
    multiple X screens after all monitors were unplugged from one of the
    X screens.
  * Fixed a bug in nvidia-settings that caused the display configuration
    page to show extra disabled displays after connecting a new monitor.
  * Added X configuration options "3DVisionProHwButtonPairing",
    "3DVisionProHwSinglePairingTimeout", "3DVisionProHwMultiPairingTimeout",
    and "3DVisionProHwDoubleClickThreshold" to configure hardware button
    based pairing in NVIDIA 3D Vision Pro. See "Appendix B. X Config Options"
    in the README for more information.
  * Fixed a bug that prevented initialization of the NVIDIA 3D Vision or
    NVIDIA 3D Vision Pro hub if no EDID was present.
 -- Brandon Snider <email address hidden>   Thu, 21 Jul 2011 21:20:31 -0400


---

### Post by Harry33 on 2011-07-22
> **VinDSL said:**
> Interesting!

Updated already...  :D

Try beta driver 280.04 from xorg-edgers PPA.
That works very well.

---

