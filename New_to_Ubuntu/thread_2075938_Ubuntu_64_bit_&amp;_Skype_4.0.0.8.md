---
title: "Ubuntu 64 bit &amp; Skype 4.0.0.8"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Mika07 on 2012-10-24
Having trouble installing Skype, the old 2.1 Beta worked ok but there's something wrong somewhere with the new version ?

Error message :

Unpacking skype (from .../skype_4.0.0.8-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/skype_4.0.0.8-1_amd64.deb (--unpack):
 trying to overwrite '/etc/dbus-1/system.d/skype.conf', which is also in package skype-bin:i386 4.0.0.8-0oneiric1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/skype_4.0.0.8-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas ? :(

---

### Post by boogerama on 2012-10-24
I'm running 4.0.0.8 on 64 bit 12.04 but had no issues loading it.  I downloaded it from Skype's site and loaded it via the Software Center.

---

### Post by mikewhatever on 2012-10-25
Do you have an older version of Skype installed? If so, try removing it first. Incase you aren't sure, run
```
dpkg -l | grep skype
```

---

### Post by Mika07 on 2012-10-25
Yeah I did that too I think I figured out :) I purged Skype and downloaded from Skypes own site and it still gave me the same error. It was about then I realised that there is no native 64 bit skype for Linux, any way I have no idea how drunk I must have been but all ia32-libs were missing ROFL! <snip> It's working now thanks guys :)

---

### Post by squakie on 2012-10-25
> **boogerama said:**
> I'm running 4.0.0.8 on 64 bit 12.04 but had no issues loading it.  I downloaded it from Skype's site and loaded it via the Software Center.
+1, using 12.10

---

