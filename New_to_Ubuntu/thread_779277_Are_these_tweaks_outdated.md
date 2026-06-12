---
title: "Are these tweaks outdated?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by skymera on 2008-05-02
I've been Googling for Ubuntu tweaks and what'not.

I've noticed only a few sties reccomend the following:
Im curious, are these needed now? or are they default in Ubutnu 8.04?

1. Ok the first is to add this to GRUB - qlevator=cfq

2. Is adding making Ubuntu use dir_index needed?

3. Preload and Prelink? needed? waste of time?

These seem dated and i just want to clarify they are not needed.

---

### Post by kerry_s on 2008-05-02
yes there outdated.

1. that's the default now
2. don't understand
3. can actually make things slower

the kernels are now getting to the point where things are optimized, there's no need to mess around on that end.

the biggest impact on performance is the programs. using lighter programs will give you the best results. having less things constantly running in the background will leave more resources for programs your actually using.

the best performance gain comes from a custom install, you install a base and work up from there, installing only what you use and using lighter alternatives.

i use a custom install of debian on 450mhz 256mb ram, i can comfortably work with in that 256mb ram with out getting into swap. all just using light programs, no tweaking.

don't mind the cpu, i'm listening to music on pandora.com, pic->

---

### Post by skymera on 2008-05-02
Nice :)

Yeah dir_index is apparently a EXT3 tweak? bit like changing the Journaling method.

Not sure if it applies

---

### Post by kerry_s on 2008-05-02
> **skymera said:**
> Nice :)

Yeah dir_index is apparently a EXT3 tweak? bit like changing the Journaling method.

Not sure if it applies

ohh, okay. i only use the noatime and i do that during partitioning. but you can add it, if you didn't do it then. i use ext2, so no journaling on my end, much faster for my old rig.

---

