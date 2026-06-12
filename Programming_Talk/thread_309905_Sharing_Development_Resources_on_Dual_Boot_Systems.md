---
title: "Sharing Development Resources on Dual Boot Systems"
date: 2006-11-30
forum: Programming Talk
---

### Post by Jamie Jackson on 2006-11-30
I do Web development (Java, CFML, etc.), and I use mainly Eclipse for development.

I'm wondering how to best share the resources between the two machines.

For instance, it would be nice to share eclipse project files, or even the workspace itself.

Similarly, it would be nice to share the apache configuration files (and anything else of apache that's pertinent).

Likewise, anything from the CFMX (JRun) that I can share between the two would be nice.

For libraries (such as Java jars), I should be able to put those in a mutually accessible area, and use environment variables to manage their access on both platforms. I don't know if this will work out or not...

Anyway, I'm just probing to find out if anybody successfully shares this stuff between OSes, and what their tricks are.

Any feedback would be appreciated.

Thanks,
Jamie

---

### Post by bernied on 2006-11-30
Have you tried a FAT32 partition (use FAT filesystem because there are no permissions to trouble you and both OSes can use it without hiccups). On Windows it will show as another disk (like D:), and you can mount it how you like on linux. Just set up your /etc/fstab.

---

### Post by bernied on 2006-11-30
oops, sorry didn't read your post right, thought you were asking about two OSes on the same machine.

ok, so maybe a samba share is the way forward. Or even nfs ?

---

### Post by Jamie Jackson on 2006-11-30
Hi bernied,

I am indeed on the same machine (dual booting XP & ubuntu). I already have a fat32 partition set up for sharing, so that's not my dilemma. Rather, I'm trying to figure out the best way to make use of the most resources across both systems.

That is to say, I'd be interested in having, say, the same Apache config work on both platforms. A prerequisite would be that I'd need to be able to reference the docroots the same way on both OSes.

So, for this case, would it be a matter of using: environment variables, local shares, clever linux mount points that match windows conventions, etc.?

I don't know the best approach, but figure that someone has tried sharing, say, apache config and sites between OSes.

Background: I'm in an all-M$ workplace, and don't think I'd have much problem switching to Ubuntu exclusively. However, I often have to support other developers who do their work on M$. Therefore, I need to be able to drop into my XP environment every now and them to walk them through some M$ configuration issue. I'd rather not maintain two sets of configs across platforms, and am looking to leverage as much as possible between the two environments.

Thanks,
Jamie

---

