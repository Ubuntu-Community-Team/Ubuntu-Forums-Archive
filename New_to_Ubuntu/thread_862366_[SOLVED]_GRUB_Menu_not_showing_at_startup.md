---
title: "[SOLVED] GRUB Menu not showing at startup"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by stalkier on 2008-07-17
I am using Ubuntu 8.04, all current updates to July 17th. When I boot my PC I do not get a GRUB menu to choose Kernals. I do not need this right now, but would like to have the option if needed. 

Other info:
I edited my boot file so that I do not get a GUI startup bar (Ubuntu Logo with statusbar). This sped my startup by about 45seconds - 1 minute. 
I am running Ubuntu Studio with real-time kernal.

System specs:
AMD Athlon XP+ 1.54GHrz OC'ed
1.5GB DDR (400Mrz)
128MB AGPx8 Slot ATI Graphics card
40GB Primary IDE (Ubuntu)
80GB NTFS (file storage)

Regards
John

---

### Post by philinux on 2008-07-17
Install and run startupmanager. It's in synaptic.

Nice gui for changing boot up stuff, it's pretty self explanatory when you run it.

The menu item ends up in system>Admin.

---

### Post by Morpheun on 2008-07-17
> **stalkier said:**
> 
I edited my boot file so that I do not get a GUI startup bar (Ubuntu Logo with statusbar). This sped my startup by about 45seconds - 1 minute. 
I am running Ubuntu Studio with real-time kernal.
John

Show us the current text of the file?

EDIT: Philinux's solution will probably work too.

---

### Post by stalkier on 2008-07-17
> **philinux said:**
> Install and run startupmanager. It's in synaptic.

Nice gui for changing boot up stuff, it's pretty self explanatory when you run it.

The menu item ends up in system>Admin.

Worked like a charm. I also kept the "Show Text at Startup" ticked so that it would speed it up just a tad. Also thank you very much for telling me about this. I now see where you can use different GRUB backgrounds etc. Pretty cool. I also found it very easy to use. Thanks again.

---

### Post by philinux on 2008-07-17
> **stalkier said:**
> Worked like a charm. I also kept the "Show Text at Startup" ticked so that it would speed it up just a tad. Also thank you very much for telling me about this. I now see where you can use different GRUB backgrounds etc. Pretty cool. I also found it very easy to use. Thanks again.

Good news then, you might as well mark your thread solved.

---

### Post by stalkier on 2008-07-17
> **philinux said:**
> Good news then, you might as well mark your thread solved.

:D On my way bud.

---

