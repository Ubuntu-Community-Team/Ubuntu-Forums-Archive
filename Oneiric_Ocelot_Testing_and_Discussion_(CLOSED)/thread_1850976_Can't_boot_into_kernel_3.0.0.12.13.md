---
title: "Can't boot into kernel 3.0.0.12.13"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by FishRCynic on 2011-09-27
Updated earlier today
Cannot boot into kernel 3.0.0.12
nor into its recovery 

No problem with 3.0.0.11

generic on amd64

anyone else have this issue?

---

### Post by JHCKX on 2011-09-27
> **FishRCynic said:**
> Updated earlier today
Cannot boot into kernel 3.0.0.12
nor into its recovery 

No problem with 3.0.0.11

generic on amd64

anyone else have this issue?
I can boot but my cursor isn't visible. I could see the menu's respond (using Gnome Classic) but no cursor visible.

---

### Post by dino99 on 2011-09-27
maybe purge then reinstall it, or try with either nomodeset or noacpi on the boot line

---

### Post by cecilpierce on 2011-09-27
I had that problem to -12 didn't generate the initrd.img all the way for some reason so I booted into the -11 and went to synaptic and reinstalled the whole -12, then it was OK.

---

### Post by FishRCynic on 2011-09-27
didn't work with kernel reinstall. dkms error message

uninstalled nvidia-current and reinstalling it did the trick.

---

### Post by cecilpierce on 2011-09-27
> **FishRCynic said:**
> didn't work with kernel reinstall. dkms error message

uninstalled nvidia-current and reinstalling it did the trick.

Great!
Now that you mention it I had that error after I installed the -12, sorry forgot, at the time I just wanted to get the new kernel working, glad you got it going   :D

---

