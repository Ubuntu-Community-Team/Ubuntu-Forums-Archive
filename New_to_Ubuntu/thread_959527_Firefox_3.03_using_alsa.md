---
title: "Firefox 3.03 using alsa"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by UpSignal on 2008-10-26
Hello there. I'm trying to fix the well known problem "flash makes firefox shutdown".
So, according to the fix, i must install alsa over the pulse audio and make firefox using it. Now that's when my problem comes in. 
The command to do it is: 

> sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”aoss”

The problem is, the file doesn't exist. I remember this file however, it must have been present on previous versions of firefox. But it isn't there nomore. How can i change the audio now?

By the way, after this, i must do the following:

> 1. Open the firefox file...

    Ubuntu users: sudo gedit /usr/bin/firefox

    Kubuntu users: sudo kate /usr/bin/firefox

2. Add the following line as last but one line of the file:

    export XLIB_SKIP_ARGB_VISUALS=1

3. Restart Mozilla Firefox

Anyone here really got this issue fixed, by doing that? thanks

---

### Post by chrisod on 2008-10-26
I uninstalled Pulse Audio and went with ALSA. It made the crashes less frequent, but they still happen occasionally. I think it's simply a hazard of depending on closed source software. We are at the mercy of Adobe, so I don't expect to ever have flawless flash performance on Linux. It simply is not important to Adobe, Inc.

---

### Post by newton93 on 2008-10-26
> **UpSignal said:**
> Hello there. I'm trying to fix the well known problem "flash makes firefox shutdown".
So, according to the fix, i must install alsa over the pulse audio and make firefox using it. Now that's when my problem comes in. 
The command to do it is: 



The problem is, the file doesn't exist. I remember this file however, it must have been present on previous versions of firefox. But it isn't there nomore. How can i change the audio now?

By the way, after this, i must do the following:



Anyone here really got this issue fixed, by doing that? thanks


In system -> preference -> sound 
you can change system's default sound, egg i use also trough that, so no hard work and simplicity

---

