---
title: "Windows vs Linux - Hard Drive Space"
date: 2007-05-20
forum: Other OS Talk
---

### Post by newlinux on 2007-05-20
One thing I've been curious about -- In my experience

 1. Windows OS installs take up much more space than linux.
 2. Windows programs require more hard drive space than linux. I mean I've installed every piece of software I want in linux and none of my machines have surpassed 5GB on the root partition.


Are these things true? If so why? What about OS X?

---

### Post by Adamant1988 on 2007-05-20
Windows installations take up more space because there is more in them, a lot more.. 

The files for them are bigger because the .exe programs typically include most (or all) of their dependencies. 

Mac OS X is uhm, I'm not sure, and their packaging format is about the same.

---

### Post by newlinux on 2007-05-20
I figured windows installations had more in them, but why? I know it's proprietary, but if anybody knows I'd appreciate it. Is it drivers, DRM code :), what? My confusion comes from the fact that it doesn't seem to do more than linux, so what is the more in it? Is it just due to the complexity that has worked it's way into the OS?

Thanks.

---

### Post by Henry Rayker on 2007-05-20
> **newlinux said:**
> I figured windows installations had more in them, but why? I know it's proprietary, but if anybody knows I'd appreciate it. Is it drivers, DRM code :), what? My confusion comes from the fact that it doesn't seem to do more than linux, so what is the more in it? Is it just due to the complexity that has worked it's way into the OS?

Thanks.

This was actually addressed by Adamant...the fact that they package their dependencies with the application is one cause for this. You know when you update (or install) a piece of software through synaptic, it checks and adds the dependencies? This just means you didn't already have an app who required those dependencies (libraries, functions, images, whatever). In the Windows world, they don't share libraries like we do, so they are included in each and every program that is installed.

---

### Post by newlinux on 2007-05-20
> **Henry Rayker said:**
> This was actually addressed by Adamant...the fact that they package their dependencies with the application is one cause for this. You know when you update (or install) a piece of software through synaptic, it checks and adds the dependencies? This just means you didn't already have an app who required those dependencies (libraries, functions, images, whatever). In the Windows world, they don't share libraries like we do, so they are included in each and every program that is installed.

Okay. I thought that referred to additional apps, but it applies to anything in the base install too (the dependencies). What purpose do DLLs serve then? I supposed those are still bloated with extra dependencies.

---

### Post by Henry Rayker on 2007-05-20
DLLs are confusing. For some apps (AOL Instant Messenger, for example) has its own DLLs for all sorts of crap...none of them are shared with any other apps. Some apps use them to share between apps, but, in order to get that, "it just works" feeling, the .exes typically don't rely on this too much. Most of the DLLs are just OS-provided and available to the apps.

---

### Post by newlinux on 2007-05-20
Thank you for the information.

---

