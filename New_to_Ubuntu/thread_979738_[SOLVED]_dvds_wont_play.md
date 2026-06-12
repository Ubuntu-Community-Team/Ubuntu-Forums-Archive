---
title: "[SOLVED] dvds wont play"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by taith on 2008-11-12
hey everyone...

using ibex... fresh install... and EVERY video dvd i put in, gives me this error... i can see the files there via the file browser...

```
taith@craig:~$ vlc /media/cdrom
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/taith/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
```

---

### Post by Linux user 66 on 2008-11-12
Have you installed *non-free-codecs* and *libdvdcss2* in the Synaptic Package Manager by enabling *[http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non free* under the *Third-Party Software* tab in the Software Sources application?

---

### Post by taith on 2008-11-12
easy fix :-) thanks!

---

