---
title: "Running Memtset86+ in Hardy"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Stunt Double on 2008-05-05
I'm trying to run memtest86+ on Hardy with known good memory. It runs until Test #3 then stops. No errors are shown but that test stays on 0 %.
  Is there a work around?
Also how do I run memtester? It's command line and typing memtester alone doesn't do it.
Thanks

---

### Post by njparton on 2008-05-08
memtest86 is a dos program that needs to run from it's own bootable disk not from within an OS?

---

### Post by skymera on 2008-05-08
Maybe try the Memtest86+ disc?

I've never personally used it so i can't help too much.

@njparton - Ubuntu installed with Memtest and it's availible at GRUB menu.

---

### Post by Sef on 2008-05-08
Here's the [memtest86]("http://memtest86.com/") site, it explains about the test.

---

### Post by njparton on 2008-05-08
> **skymera said:**
> 
 
@njparton - Ubuntu installed with Memtest and it's availible at GRUB menu.
 
I've stared at that screen soooo often yet completely missed that entry! :oops:
 
+1 for trying the memtest cd instead.

---

### Post by Stunt Double on 2008-05-11
I tried Memtest86+ via the GRUB menu and also via CD. With both memory slots used, it wouldn't run. It looks like there is a problem with the second memory slot on the motherboard.
With only the first slot in use, Memtest86+ does work and the computer no longer freezes intermittently at boot (which is why I wanted to test the memory). I put a 512MB stick in the first slot and won't use the second slot. 
Thanks for the help.

---

