---
title: "Should my /lib/modules and /usr/src keep growing?"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by clskier on 2013-06-11
I built my own NAS about six months ago running on Ubuntu Server 12.10 running just simple things like Samba, FTP, Squeeze Box server, Plex Server, and also XBMC.  When I had it all working the OS with XBMC itself was only about 4Gb, so I shrank my partition down to 8Gb and ghost it onto a thumb drive once a month.

The total size of my root partition has been growing over the past six months and now encompasses close to the entire 8Gb.  I see the /lib/modules and the /USR/SRC directories combine to about 4Gb of that size and contain several versions of the same file.  Is this normal?

I guess I am just wondering if I should be doing anything to keep this down when updates occur, or am I crazy to expect my install to remain under 8Gb.  I can increase the size of my root partition if that is the correct thing to do.  Just wondering if I should expect this to keep growing at this rate.

Thanks

---

### Post by Impavidus on 2013-06-11
Try to uninstall some old kernels and old headers using your favorite package manager. The packages are named **linux-headers-<some version>** and **linux-image-<some version**. But I have the impression they are growing a bit faster than they ought to.

---

### Post by clskier on 2013-06-11
Thanks, that freed up tons of space

---

