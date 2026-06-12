---
title: "[SOLVED] Restricted Modules + Grub Cleanup"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-07
Hi,
Basically i'd like to get a noob definition of the restricted modules. Also, when booting, my grub just has too many entries for my liking. I'd like a sudo, if one exists or some synaptic guidance to remove all unnecessary kernel versions(or images) so i just remain with 2.6.24-19 (my current, works fine) and -18.
If it's at all possible. Or am i conspiring to break my system ? :)

---

### Post by iaculallad on 2008-07-08
To clean your GRUB menu list from displaying OLD kernel boot options, navigate to System->Administration->Synaptics Package Manager. Click on "Search" and enter "linux-image" (that's without double quote) as search string. All kernels will be displayed and do a right-click on the kernel you want removed and select "Mark for Complete removal". Perform the process on other kernels, and once finished selecting, click on "Apply". This will automatically reconfigure your GRUB menu, deleting kernels that your had removed.

NOTE: Leave one kernel just in case.

---

### Post by BGFG on 2008-07-08
nah i think i'll leave the latest two to be safe. Using 'complete removal' says that it will also remove the -rt modules associated with -16 and -17. Just to be sure, could any of my current packages be dependent on the restricted modules of the older kernels ? I don't think so, but better i look dumb than not ask at all.

---

### Post by funkydan2 on 2008-07-08
Nope.  The restricted modules for the -16 kernel are **only** used when you're running (boot using) the -16 kernel.  So go ahead a delete any kernel you no longer use - but you're wise to be cautious, better to ask a question than screw up your machine.

---

