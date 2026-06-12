---
title: "Is there anything in particular I ought to do upon a fresh install of Intrepid Ibex?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by wracktail on 2008-11-02
I've installed the newest version several times now, and each time I've run into some graphical issues that I hadn't run into with Hardy Heron. The title bar glitches out on me, typically blanking entirely. It only happens, so far as I've noticed, once I install the proprietary drivers from NVIDIA, but both 173 and 177 cause it. Is there anything in particular I'm missing?

---

### Post by jbrown96 on 2008-11-02
Are you using 177.80? Intrepid has a new version of X server. The older drivers will not work. Just use the ones from the hardware drivers app; it will save you a lot of trouble. If you are still having trouble, post back with the exact version number and your video hardware with ```
 lspci | grep VGA 
```

---

### Post by mikewhatever on 2008-11-02
There seems to be an issue with the new Compiz. Disabling desktop effects solves the problem, at least till there is a fix.

---

### Post by wracktail on 2008-11-02
> **jbrown96 said:**
> Are you using 177.80? Intrepid has a new version of X server. The older drivers will not work. Just use the ones from the hardware drivers app; it will save you a lot of trouble. If you are still having trouble, post back with the exact version number and your video hardware with ```
 lspci | grep VGA 
```

I'd been installing the driver via the Hardware Drivers application, though I've also tried installing the packages from .deb; I don't suppose that's in any way related to the issue. I don't know what way I might possibly describe it except to say that the title bar blanks out for, seemingly, no reason at all, and it happens with both 173.14.12-1-0ubuntu4 and 177.80-0ubuntu2. I don't know how to use launchpad very well, or I'd see if I could find some reference to it there.

That being said, ```
koopatrol@sirius:~$ lspci | grep VGA
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
```

---

### Post by wracktail on 2008-11-02
> **mikewhatever said:**
> There seems to be an issue with the new Compiz. Disabling desktop effects solves the problem, at least till there is a fix.

Is there any indication what the source might be? For instance, might I be able to bypass the issue by installing an old version of compiz?

---

### Post by shane19174 on 2008-11-02
> There seems to be an issue with the new Compiz. Disabling desktop effects solves the problem, at least till there is a fix.

There's no problem with compiz (running extra effects) here with nvidia 177.80. I think the problem might lie elsewhere. You said you've installed Intrepid several times. Does this mean clean install or upgrade? Either way, are you using a user profile from an earlier install? Try a fresh user and see if you get the same thing.

---

### Post by wracktail on 2008-11-02
> **shane19174 said:**
> There's no problem with compiz (running extra effects) here with nvidia 177.80. I think the problem might lie elsewhere. You said you've installed Intrepid several times. Does this mean clean install or upgrade? Either way, are you using a user profile from an earlier install? Try a fresh user and see if you get the same thing.

It's been a clean install every time; upgrades are something I try to avoid whenever possible. I've formatted completely each time, bringing nothing from the former system over.

At this point, I am more convinced of the idea that it's compiz rather than NVIDIA, as per mikewhatever. The problem doesn't arise if I leave my Appearance>Visual Effects setting at None even after I've enabled the proprietary drivers.

---

### Post by shane19174 on 2008-11-02
Hmm, like I said, no problem with compiz here... Are you using the default theme? Could it possibly have anything to do with themes or the underlying engines, or is this reproducible no matter what appearance settings (other than compiz effects) you choose?

May not be relevant at all, just trying to narrow things down...

---

### Post by wracktail on 2008-11-02
> **shane19174 said:**
> Hmm, like I said, no problem with compiz here... Are you using the default theme? Could it possibly have anything to do with themes or the underlying engines, or is this reproducible no matter what appearance settings (other than compiz effects) you choose?

May not be relevant at all, just trying to narrow things down...

I actually had the same idea, tested it, and came here to mention it. :D

The error seems to come about particularly when I move the mouse over the min/max/close buttons. I've included a screencaps this time around to try to better show what exactly is going on. The content of the title bar either disappears entirely, as shown, or scratches out, with parts showing, and parts not, black or blank lines running through.

---

### Post by mikewhatever on 2008-11-03
> **wracktail said:**
> Is there any indication what the source might be? For instance, might I be able to bypass the issue by installing an old version of compiz?

I don't know, but a solution has been suggested in another thread, take a look. [http://ubuntuforums.org/showthread.php?t=875741&highlight=compiz+title+bar](http://ubuntuforums.org/showthread.php?t=875741&highlight=compiz+title+bar)


> **shane19174 said:**
> There's no problem with compiz (running extra effects) here with nvidia 177.80. I think the problem might lie elsewhere. You said you've installed Intrepid several times. Does this mean clean install or upgrade? Either way, are you using a user profile from an earlier install? Try a fresh user and see if you get the same thing.

Well, I didn't mean the problem with the new compiz is global. Some users are affected, others aren't. I've also thought it might be the settings carried over from Hardy (separate /home in my case), but creating a new user didn't fix it.

---

