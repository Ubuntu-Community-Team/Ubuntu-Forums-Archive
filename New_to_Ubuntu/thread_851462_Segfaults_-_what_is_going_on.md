---
title: "Segfaults - what is going on?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-06
Does anyubody know what is going on here and why?


Jul  7 01:48:17 PJ kernel: [ 5347.885373] ipw2200: Firmware error detected.  Restarting.
Jul  7 09:13:51 PJ kernel: [ 9004.056383] ipw2200: Firmware error detected.  Restarting.
Jul  7 09:49:16 PJ kernel: [ 4652.955878] firefox[5854]: segfault at b789831a eip b7d6f2a5 esp bf8fed40 error 4
Jul  7 09:49:16 PJ kernel: [ 4653.395152] firefox[5856]: segfault at b789831a eip b7d6e2a5 esp bfe842c0 error 4
Jul  7 09:49:33 PJ kernel: [ 4658.631743] firefox[5870]: segfault at b780f31a eip b7cfa2a5 esp bfa5a6a0 error 4
Jul  7 09:49:33 PJ kernel: [ 4658.964906] firefox[5872]: segfault at b784231a eip b7d462a5 esp bfb92fd0 error 4
Jul  7 09:49:56 PJ kernel: [ 4664.182429] firefox[5886]: segfault at b784231a eip b7d502a5 esp bfde6a20 error 4

---

### Post by Tatty on 2008-07-06
Are many applications crashing with a segmentation fault? This usually indicate a hardware problem, most likely RAM.

Try running a memory test on your system (you should be able to select this as an option in grub.

---

### Post by dunbrokin on 2008-07-06
> **Tatty said:**
> Are many applications crashing with a segmentation fault? This usually indicate a hardware problem, most likely RAM.

Try running a memory test on your system (you should be able to select this as an option in grub.

I ran memtest for an hour and no errors showed....Only FF shows the segfault.

---

### Post by neurostu on 2008-07-06
There is a possibility that the CD you used to install had some errors on it. This happened to me once... I had to reburn the iso and reinstall for the seg faults to go away.

---

### Post by dunbrokin on 2008-07-06
> **neurostu said:**
> There is a possibility that the CD you used to install had some errors on it. This happened to me once... I had to reburn the iso and reinstall for the seg faults to go away.

Hmmm, that is a possibility I had not thought of....but why would it only happen with FF. My install was in April...and there have been lots of updates since then...and the only problem I can find is with FF.

---

