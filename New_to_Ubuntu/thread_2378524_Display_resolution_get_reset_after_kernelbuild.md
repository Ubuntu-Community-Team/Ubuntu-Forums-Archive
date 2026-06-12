---
title: "Display resolution get reset after kernelbuild"
date: 2017-11-24
forum: New to Ubuntu
---

### Post by botckris on 2017-11-24
Hi everyone, sorry not very familiar with Linux
I'm currently working on a project on Linux-4.4.94 kernel while my original Ubuntu16.04 is built-in with 4.10.0
so I do the kernelbuild and install the new kernel. 

But after booting into the new kernel I found out that the display resolution get reset to 1024x768 and I cannot change it. ([old]("https://imgur.com/g1fssJB") v[IMG]https://imgur.com/g1fssJB[/IMG]s [new]("https://imgur.com/ZE5RchE"))
I also found out there's a message said "snd_hda_intel 0000:00:1f.3: failed to add i915 component master(-19)" while booting up and I doubt this is the reason.

I only have [COLOR=#003C71][FONT=intel-clear]Intel® HD Graphics 630 [/FONT][/COLOR]on my computer (built-in the CPU)
and I enable the **Intel 8xx/9xx/G3x/G4x/HD Graphics **options in the menuconfig but still have the same error.

Hope someone can help me fix this problem, 
thanks for the help!!

---

### Post by botckris on 2017-11-27
bumped is anyone had this issue before ?

---

