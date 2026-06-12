---
title: "Pandora stopped working in Chromium?"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by aem0512 on 2012-04-26
I have been using Pandora on Chromium in Ubuntu 10.04 for a few weeks now without any problems, but a couple of days ago it just stopped working. 

Occasionally something like this will happen on my linux computers, where a flash website will totally crash the browser every time I try to go to that page thereafter. Even after cleaning out browser history, stored passwords, cookies, etc...

Pandora doesn't crash the browser though, it just keeps telling me to reload, but it never works. I've cleaned out browser data from Chromium. 

Any tips?

---

### Post by bpodgursky on 2012-04-26
No tips, but pandora also stopped working for me in chromium (v 18.0.1025.151) a few days ago on ubuntu 11.10.

---

### Post by pissedoffdude on 2012-04-27
What version of flash player are you running?  Are running the 64-bit version of ubuntu?  What type of graphics card do you have, and which drivers are currently installed.  Also, is this issue only specific to chromium, or is firefox affected as well?

The latest flash player has issues with nvidia graphics cards.  You can "fix" this by disabling the video overlay

You can disable it by creating an xsession script and adding```
export VDPAU_NVIDIA_NO_OVERLAY=1
``` to ~/.xinitrc, or you can simply create a script for chromium so that the overlay is only disabled in chromium: ```
#!/bin/bash
export VDPAU_NVIDIA_NO_OVERLAY=1
/usr/bin/chromium
```  (note: this only applies if you have an nvidia graphics card)

If you have any issues with a blue tint in your videos, make sure hardware acceleration is enabled in flash by verifying you have ```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true
``` in /etc/adobe/mms.cfg

---

### Post by rburkartjo on 2012-04-27
i have the same problem. and cant get pithos to load either they say it is a problem with pandora.

---

### Post by rburkartjo on 2012-04-27
it still works great in firefox 12.0

---

### Post by kly546 on 2012-04-27
Same problem here. Pandora plays one song then stops. Running Chromium 18.0.1025.151 on Debian Wheezy. I emailed Pandora support to alert them they changed something. Just watch, instead of fixing their problem they will blame it on my browser or OS.

---

### Post by bplzip on 2012-05-01
Read all about the problem with Pithos here:
 [https://bugs.launchpad.net/pithos/+bug/988395]("https://bugs.launchpad.net/pithos/+bug/988395")

Seems that the Pithos team is close to releasing a fix.

---

