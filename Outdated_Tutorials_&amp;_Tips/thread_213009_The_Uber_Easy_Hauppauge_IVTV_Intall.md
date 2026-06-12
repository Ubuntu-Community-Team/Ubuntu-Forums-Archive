---
title: "The Uber Easy Hauppauge IVTV Intall"
date: 2006-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by mckryptyk on 2006-07-10
This way of installing the IVTV drivers will work for i386 and x64 architectures because *You'll be compiling it* :p 

Don't worry, Apt-get is your friend on this one, so let's begin.

** This has been shamelessly ripped from [http://ivtvdriver.org/index.php/Howto:Ubuntu]("http://ivtvdriver.org/index.php/Howto:Ubuntu") **
**DONT FORGET **
[B]When the guide makes mention of "/usr/lib/hotplug/firmware/" 
If your using Dapper, replace it with "/lib/firmware/"
Everything else should be followed.[/B]

*For example: *

```
cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
```

*Should be:*

```
cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
```

```
 ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw 
```

**At the end of this, be sure to reboot and in terminal type:**
```
dmesg | grep ivtv
```
*This will show if there are errors if you see none  Great! :)*

---

