---
title: "Problem with updating VLC in 8.10"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-10-26
When I had 8.04 installed I went ahead and installed the latest version of VLC, then last night I installed the latest version of ubuntu 8.10 and now when I try to get VLC working (it didnt work initially so I completely removed all of VLC then reinstalled from the main repo), when I run synaptic to reinstall the latest version I get this error.
> 
[B]E: /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_i386.deb: trying to overwrite `/usr/lib/libvlccore.so.0.0.2', which is also in package libvlc0
E: /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_i386.deb: trying to overwrite `/usr/lib/libvlc.so.2.0.2', which is also in package libvlc0[/B]

Greek to me, is there a conflict here? I clicked on "fix broken packages" in synaptic but that didnt do anything.

Ideas?

---

### Post by markharding557 on 2008-10-26
using sudo natilus try removing all instances of libvlc and any other things to do with vlc

---

### Post by wolfen69 on 2008-10-26
> **markharding557 said:**
> using sudo natilus try removing all instances of libvlc and any other things to do with vlc

```
gksudo nautilus
```
doing ```
locate vlc
``` will help.

---

### Post by VitaminBB on 2008-10-26
Wow that was annoying, that did it!

Thanks guys!

---

### Post by markharding557 on 2008-10-29
> **wolfen69 said:**
> ```
gksudo nautilus
```
doing ```
locate vlc
``` will help.

tested the locate command out and this is way quicker than the search function in nautilus good call

---

### Post by Miguellint on 2008-10-29
> **markharding557 said:**
> tested the locate command out and this is way quicker than the search function in nautilus good call

The locate command works off a file-name database which gets updated daily-ish (depending on your configuration). It doesn't actually look through the hard disks etc for your file, just through the database. It is quick but may not be aware of files created in the last day or so.

You may want to run...

sudo updatedb 

...before using locate. This command updates the database of file names.

I also read somewhere you should use sudo when you use locate. Not too sure why. Something to do with checking more than just your home folder I guess.

Regards

---

