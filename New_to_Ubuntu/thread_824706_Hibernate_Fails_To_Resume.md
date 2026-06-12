---
title: "Hibernate Fails To Resume"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Kralnor on 2008-06-10
I'm running 8.04 Heron and it seems like neither suspend nor hibernate can properly resume. After resuming the process doesn't get any further than "Suspending Console(s)". Either that happens or there is simply a black screen.

I suspect a recent kernel update in Synaptic messed it up. Can anyone confirm that?

**[This bug report](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/219675)** seems to suggest that it has been fixed in linux-image-2.6.24-19-generic, 2.6.24-19.33 - how do I manage to upgrade?

---

### Post by philinux on 2008-06-10
You'll have to tick proposed updates in software sources.

---

### Post by Kralnor on 2008-06-10
Already done.

---

### Post by philinux on 2008-06-10
Well I've not installed them yet as I'll have to re-compile my graphics driver. I'm holding off until they're mainstream.

Change your server to main and reload. Then click check.

---

### Post by Kralnor on 2008-06-10
The update still doesn't show up.

---

### Post by philinux on 2008-06-10
Thats odd.

Just double check in Software Sources under the updates tab that proposed is ticked.

---

### Post by user17 on 2008-07-08
"Suspending console(s)" was the message frozen on my screen when unsuccessfully attempting to suspend (I didn't try hibernate). It was not a resume problem- that's what I have now, with the traditional blank screen. 

I fixed the "Suspending console(s)" problem by -I think- installing drivers for my bcm4318 wifi card. System log had indicated to me that my wifi card was a problem around the times when I tried to suspend.

---

