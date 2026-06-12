---
title: "[SOLVED] Booting into low-graphics mode?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rudedoggx on 2008-06-06
As of yesterday, my PC has been booting into low-graphics mode.  I'm not qutie sure what caused this, but It will not change back.  Yes, I have already updated my video driver.
My graphics card is an ATI Radeon 9550, and it was working just fine yesterday..

---

### Post by hyper_ch on 2008-06-06
hmmm

(1) backup your xorg.conf

```

sudo cp /etc/X11/xorg.conf xorg.conf.back

```

(2) reconfigure x11
```

sudo dpkg-reconfigure xorg-server -phigh

```

(3) reboot (or restart xserver)

if that does not help, copy the backed up xorg.conf.bak back to its orginal state.

---

### Post by rudedoggx on 2008-06-06
Package `xorg-server' is not installed and no info is available.

What does that mean?

---

### Post by hyper_ch on 2008-06-06
oh, it's:

xserver-xorg

---

### Post by rudedoggx on 2008-06-06
That seemed to solve the problem of 'low-graphics' mode, however, I'm now presented with a new problem.  Whenever I scroll on this webpage (or any other) the page refreshes.  I mean, whenever I try to scroll slightly the page takes about a second to refresh, it just isn't smooth. My monitor (or something) is making a very light high-pitched noise when it does this refreshing..

Also, my Graphics driver just uninstalled itself and is now 'not in use'? Should I update it again?

---

### Post by hyper_ch on 2008-06-06
try to update it again.

Or get a non-ati card ;)

---

### Post by sayakb on 2008-06-06
Change the refresh rate to a higher value: System->Preferences->Screen resolution
Disable dual monitors if enabled.

---

### Post by rudedoggx on 2008-06-06
Updating the driver did the trick, how do I mark this as solved?

What would you recommend for a video card?

---

### Post by sayakb on 2008-06-06
Thread tools (@ top of thread)->Mark thread as solved.

---

### Post by hyper_ch on 2008-06-06
well, intel seems to be least problematic so far on linux.... nvidia - with the binary drivers - works also quite good.... ati just sux...

However I think I heard that ati is going to opensource their drivers soon - or something similar - so from then on ati will probably be best for linux... it is not at this moment.

But good the problem got solved.

---

