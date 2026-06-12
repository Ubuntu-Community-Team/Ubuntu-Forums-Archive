---
title: "Preload applications to RAM at boot time"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by newb85 on 2014-01-28
Currently, I'm running Ubuntu Saucy on an old desktop machine (Dual-core, 2GB RAM).  It handles the system fine, for the most part.

However, I would like to improve the time applications take to load.  Mostly, I use Chrome and Evolution, and sometimes LibreOffice apps.  I installed preload with the understanding that that was the purpose--to automatically load frequently used programs to RAM for quick access.  However, it seems that the applications I'm trying to preload (or most of them) are now designed to continue running in memory even when you close them, so that you really only ever open them once per boot up.  In other words, preload won't categorize them as "frequently used", because they're only used once per boot.

While I like the idea of a daemon that "learns" what I use frequently, I would also be fine with simply setting up a defined list to load to RAM at boot time.  I just don't know how...

Any suggestions?

---

### Post by king.of.random on 2014-01-28
I believe applications continuing to run in memory after they close is a design feature of Linux. The memory will be flushed as and when it is needed to offer more memory to the system as required. As for pre-loading applications, I'm sorry I don't have the expertise to help you there. 

Just a thought Libreoffice is a large application (still quite bloated), have you tried alternatives such as abiword if speed is your issue. Also don't forget that the extensions that you may have installed within your browser also have a payload penalty.

---

### Post by newb85 on 2014-01-28
Thanks for the suggestions.  Yes, I have given Abiword, Gnumeric, and several others a try, and I prefer LibreOffice.  The machine doesn't have trouble running these applications.  It just takes eight to ten seconds to load them the first time.  Beyond that, they generally run seamlessly.

I don't think keeping the applications in memory is a design feature of Linux in general.  It hasn't always been the case for Ubuntu.  I don't have a problem with it--I think it's a great plan.  It just doesn't improve initial load time, and it unfortunately prevents the package preload from doing so.

---

### Post by tgalati4 on 2014-01-29
You could write a script to load the applications at boot time.  With only 2GB or RAM, you could fill your RAM with too many applications open at once, which will slow things down.

Put the appropriate libreoffice command in /etc/rc.local.

```
man libreoffice
```

There are several switches to consider.

---

### Post by newb85 on 2014-02-01
I doubt I will have a problem with too many applications at once (given that I can open all three of them manually now with no problems).

Thanks for pointing to /etc/rc.local.  It looks like a good place to start.  The three applications I mentioned all have man pages; however, from reading them, I don't see a way to load any of them to memory (and not the screen), but maybe I'm missing something...

---

### Post by buzzingrobot on 2014-02-01
If you don't need to actually shutdown, just suspend.  Your apps will stay just where they are.

---

### Post by newb85 on 2014-02-02
I'm aware of that.   I didn't think of that as the optimal approach.   But maybe I should reconsider.   Regardless of whether it is preloaded automatically, the processor still has to bring up each program after a reboot before I can use them.  That's probably why Windows 8 doesn't normally really shut down.

---

