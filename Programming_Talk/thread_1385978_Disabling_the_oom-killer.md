---
title: "Disabling the oom-killer"
date: 2010-01-20
forum: Programming Talk
---

### Post by Frogging101 on 2010-01-20
I use a (sometimes) very memory intensive 3d modeling and and animation program called Blender. The problem is, when it hogs all the memory, Ubuntu's oom-killer (out of memory killer) kills it. I found a script online to protect certain processes, but if I protect blender and bash, it almost arbitrarily kills something else such as gnome.

Is there a way to disable this function of the kernel? Sorry for posting this here, but this seemed the only suitable place other than general help, and I know from experience NEVER to post there because no one answers you.

---

### Post by Hellkeepa on 2010-01-20
HELLo!

Increase the swap area, or add more RAM to your computer. If you disable the OOM-killer, all you'll end up with is a non-responding computer. Until you pull the plug on it, of course.

Happy codin'!

---

### Post by CptPicard on 2010-01-20
What do you suppose the kernel could do if it didn't kill some process when the machine runs out of memory?

---

### Post by hessiess on 2010-01-20
Buy more memory.

What version of Blender are you using and what are your system specifications.

If by any chnce you are using the 2.5 alpha, you have probably found a memory leak.

---

### Post by ideasman42 on 2011-07-18
Hi we're aware of this problem.

Its not a memory leak, blender can be made to do very large allocations - most common cases of this are:
- Compositing high res images, since we use float buffers internally for compositing.
- Misuse of subsurf modifier can end up allocating a lot of ram.

Currently blender just doesnt handle out of memory cases at all and will crash, so thats bad but not easy to fix in all cases :S.

Bottom line is you need to either optimize you're scenes, composite lower res images - which is normally not so hard.
... Or get more ram.

Longer term blender will probably move to tile based GPU compositing, which is in development currently.

---

