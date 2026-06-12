---
title: "beagled indexing at boot"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by mdsmedia on 2008-10-16
Hi,

I've used Ubuntu since 5.04 and I love it. I've recently upgraded from 6.06 to 8.04 and my computer found a new lease on life.

One issue I have is that Beagle will re-index every time I reboot. This seems to take ages and sucks a bit out of my system until it's finished.

Is there a way I can switch off automatic indexing and maybe manually switch it on, or have it only re-index less often.

I appreciate I don't have to reboot Linux as much as some other operating system, but not everything is perfect, so rebooting does happen, and I'm running it on a notebook so rebooting is probably more regular than might otherwise be. I'm running on a 1.6MHZ HP Compaq nx6120 with 512MB of RAM.

---

### Post by Paqman on 2008-10-16
Sure, just open Beagle Search > Preferences and uncheck "start indexing services automatically"

---

### Post by mdsmedia on 2008-10-16
Thanks, but where do I find Beagle Search....is it in the menus or just CLI?

---

### Post by Paqman on 2008-10-16
You should have a search icon on your top panel, otherwise the shortcut is F12. 

You can also launch apps through the terminal, or by hitting Alt-F2. In both those cases you'd launch Beagle by typing:

```

beagle-search

```

---

### Post by mdsmedia on 2008-10-17
thanks...just got back on my Ubuntu box and it was as easy as that.

BTW, I'm not completely new to this, just to beagle, which I could never get to do what I wanted to do in earlier versions....or an earlier version, but I've never really used beagle, so was completely unfamiliar with it.

---

### Post by ByteJuggler on 2008-10-17
> **mdsmedia said:**
> One issue I have is that Beagle will re-index every time I reboot. 

Are you saying it re-indexes from scratch?  I'm pretty sure that's not supposed to happen.  BTW, newer Ubuntu's have an alternate indexing/searching engine included called "Tracker".  Are you aware of this and have you tried that out?  (It's used to be the case that it was supposed to be more system friendly in terms of indexing impact as well compared to Beagle, don't know if that's still the case or not.)

---

### Post by mdsmedia on 2008-10-17
I can only guess it's indexing...let alone indexing from scratch. When I reboot, not come back from suspend, my system monitor shows something sucking a lot of resources. It goes on for ages.....haven't measured how long but I'm guessing more than an hour. Conky tells me "beagled-helper".... so I'm guessing Beagle indexing.

---

