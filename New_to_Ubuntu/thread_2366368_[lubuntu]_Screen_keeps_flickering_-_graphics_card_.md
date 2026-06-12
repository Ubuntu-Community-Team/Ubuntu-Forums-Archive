---
title: "[lubuntu] Screen keeps flickering - graphics card broken?"
date: 2017-07-17
forum: New to Ubuntu
---

### Post by aellisif on 2017-07-17
I've just installed Lubuntu on an old laptop, and while everything worked fine while I was live booting the old thing and also during the first two boots, now the screen keeps flickering and won't stop. I've run a few commands that I found in another thread which I'm attaching here, but I would be really thankful for some more advice on how to fix this issue. 

I've live booted the machine with different OS before I finally decided on Lubuntu, and the problem never arose. Now I'm worried the graphics card might be giving out on me (it is a fairly old machine).

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
```

```
uname -a
Linux neridi 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:29:33 UTC 2017 i686 i686 i686 GNU/Linux

```

```
lspci -nnk | grep -iA2 
vga01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV530/M56-P [Mobility Radeon X1600] [1002:71c5]
Subsystem: Hewlett-Packard Company Compaq nx9420 Notebook [103c:309f]
Kernel driver in use: radeon

```

```
env | grep DESK
DESKTOP_SESSION=Lubuntu
XDG_SESSION_DESKTOP=Lubuntu
XDG_CURRENT_DESKTOP=LXDE

```

---

### Post by BenginM on 2017-07-17
Salutations!

any reason you want to run 17.04 instead of 16.04 lts!

i don't see a reason yet that indicate a GPU card fault.. also is the CPU an Intel with an integrated built-in GPU! 

i suggest you try 16.04 , or install kernel 4.4, or 4.8 in 17.04 and test the behavior there .

---

