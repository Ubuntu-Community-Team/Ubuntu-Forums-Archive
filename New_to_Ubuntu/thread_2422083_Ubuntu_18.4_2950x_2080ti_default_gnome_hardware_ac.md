---
title: "Ubuntu 18.4 2950x 2080ti default gnome hardware acceleration"
date: 2019-07-02
forum: New to Ubuntu
---

### Post by stringcode2 on 2019-07-02
I have installed Ubuntu LST 18.4 **SERVER** (so that I can setup raid 0 for `/`, no raid for `/boot`). I have then installed ubuntu-desktop. No tweaks, just the default. 

Running CPU Thread-ripper 2950x, Nvidia 2080ti, 32GB corsair 3200Mhz, 2x 970 EVO, X399 MEG creation, EVGA 1300w gold. I have installed Nvidia Driver via adding Nvidia driver repo and selected 430 driver in software update app / additional drivers. I have verified that CPU, GPU, NVMEs perform at expected, sustained speeds (via indigo benchmark, Uniengine Superposition). 

And yet desktop environment feels laggy. Moving windows around seems far less smooth than expected. Is there some setting Im missing to force gnome into using hardware acceleration ? Should I be using different desktop entirely ? 

Any advice is much appreciated, thank you.

---

### Post by CatKiller on 2019-07-02
> **stringcode2 said:**
> And yet desktop environment feels laggy. Moving windows around seems far less smooth than expected. Is there some setting Im missing to force gnome into using hardware acceleration ? Should I be using different desktop entirely ? 

There are many issues with performance and perceived performance on Gnome; things like input lag and animations running at a lower refresh rate than the monitor. They're in the process of being fixed as a result of Ubuntu moving to Gnome rather than Unity and now trying to knock it into shape.

I've never used Gnome with 18.04; I know about the issues from seeing reports of them being fixed in later versions. You could look for backports or fixes, or try a different environment, depending on which you would find easiest / nicest / most interesting. Everyone has their own preferences and limits for what they'll tolerate.

Personally I've really been enjoying KDE, but you might prefer something different, or the experience of fixing Gnome.

---

### Post by stringcode2 on 2019-07-02
Would you happen to know if these fixes are on 19.xyz ? Or is it possible to update to latest gnome ? (should have the fixes included ?)  Thank you for your advice ?

---

### Post by CatKiller on 2019-07-02
> **stringcode2 said:**
> Would you happen to know if these fixes are on 19.xyz ?  
I believe they are. It might be worth trying them out from a live USB to see if it's improved for you. 

Obviously the support period is less for the non-LTS releases. 

>  Or is it possible to update to latest gnome ? (should have the fixes included ?)  Thank you for your advice ?

[Kind of.](https://askubuntu.com/questions/1072096/how-to-install-gnome-3-29-92-or-3-30-in-ubuntu-18-04) It looks a bit messy from a quick search.

---

### Post by stringcode2 on 2019-07-02
Thanks for your help. I will give 19.4 a go ! Again thank you!

---

### Post by stringcode2 on 2019-07-04
Alright I gave 19.4 a go. Performance improvements seems marginal at best. Well within the realm of placebo. Looks nicer but still feel far less smooth than I would expect given the specs of the machine. For now I'm sticking with it. But hope it will improve in the future. Thank you all for the  advice

---

### Post by rbmorse on 2019-07-04
Your patience should be rewarded.  

There are some some allegedly significant performance improvements to Mutter (Gnome's default window manager/compositor) in staging that should be making their way to the distros in the near future.  I've lost track of where they are -- can't remember if they're for 3.34 (September) or somewhere beyond that, but they're coming.  Daniel van Vugt at Cannonical leading the effort.

---

### Post by CatKiller on 2019-07-04
No problem. Happy to help.

Since you're still at the experimentation stage anyway, it might be worth trying KDE. I switched away from Gnome for reasons other than performance, and was a bit cautious about KDE having only tried it once before in the rough days at the start of KDE4, but I was surprised by how easy it was and how well everything worked. It's been really enjoyable.

---

### Post by cruzer001 on 2019-07-04
Also while at the experimental stage you can open up the "Proposed" repository for the latest unstable gnome builds.

[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

What kernel are you running?  Its possible to install the latest stable or rc kernel either from the site or PPA.

Just throwing this out there, good luck.

ps
16core...wow
Makes a die hard Xeon guy think twice :)

---

