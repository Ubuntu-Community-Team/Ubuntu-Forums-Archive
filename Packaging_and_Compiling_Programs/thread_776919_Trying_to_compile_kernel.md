---
title: "Trying to compile kernel"
date: 2008-05-01
forum: Packaging and Compiling Programs
---

### Post by s_raghu20 on 2008-05-01
Hi,

I tried to follow the kernel compilation guide at [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")  and [https://wiki.ubuntu.com/MeetingLogs/openweekhardy/UpstreamKernels]("https://wiki.ubuntu.com/MeetingLogs/openweekhardy/UpstreamKernels").

All looked good, as in git cloning happened nicely.  In the make oldconfig, I tried to act intelligent and removed/included some modules that I felt could be interesting..

however, the next step of making a package failed. And funny thing is, it complains about not finding a file, from a tree which I cloned from kernel.org...

```
ld: drivers/media/built-in.o: No such file: No such file or directory
make[2]: *** [drivers/built-in.o] Error 1
make[1]: *** [drivers] Error 2
make[1]: *** Waiting for unfinished jobs....

```

I on hardy 64bit, compiling just for experience. the very FIRST time...

anybody has seen anything like this ?

---

### Post by Bost on 2008-05-01
I'm pretty new to git but it seems like Linus's mainline kernel git tree is not compileable... 
Clone a git tree of someone else or wait until he fixes it. It might be a red letter day today so be patient...

---

### Post by Eclipse. on 2008-05-03
I have the exact same problem building from latest git.Normally I just use the source and patch but I decided to build from git for a change.

Open your .config file and search for CONFIG_DVB_CORE change it to n and it should build successfully.

---

