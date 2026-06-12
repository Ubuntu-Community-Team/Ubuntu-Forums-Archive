---
title: "Two questions about Ubuntu 14.04 LTS"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by Tar_Ni on 2014-04-29
Hi,

I have two questions about the new Ubuntu 14.04 release which I just installed a few days in my laptop.


1. Why does the update manger do no prompt me to install updates when I power on my computer and comes into my Ubuntu desktop? All is set as to prompt me ''immediately'' of any kind of updates. Do I have to wait longer? It is a habbit of mine to install updates first thing when using my computer. Now I have to get them manually.

2. I have four plug-ins of Ubuntu in my firefox, (Unity intergration, ubuntu online account ect.) Are they all needed? surely all these addons must slow down the browser?

Thanks.

---

### Post by LastDino on 2014-04-29
Hmm have you tried checking session start up options in settings? Check if ''automatically check for update'' is ticked or not.

---

### Post by Impavidus on 2014-04-29
If you selected "inform me at once" you should get an update as soon as the new updates are detected, that is directly after login if you didn't install the updates before the last shutdown or as soon as the package manager has refreshed the lists of available software (like when running apt-get update) and new updates are available. It does however not refresh the lists of available software as soon as you have booted. The package lists are updated by a script run by anacron. Anacron runs the script once a day, which is usually a few minuted past midnight or a few minutes after booting.

---

### Post by mcduck on 2014-04-29
The update check is delayed slightly to avoid the computer being unusable immediately after logging in due to all the programs starting and checking updates etc. (The typical Window problem when you see the desktop and still need to wait a bit for everything to get started before the computer is actually usable). And of course you are only offered the updates once per day (with the "immediate" option, the default is once per week apart from important security updates), so if run a manual update as soon as you can, you're never even going to get prompted for updates automatically...

My suggestion would of course be to relax a bit and let the update manager tell you when there's something to update, but if you really want to do it as the first thing right after logging in, you could always add a command in ~/.profile to check for the updates...

---

### Post by Tar_Ni on 2014-04-29
Ok thanks a lot guys, I will sit and wait and see how it goes in the next few days to get prompted automatically. :)

Other question: What is the ''Ubuntu firefox modification'' and ''Unity websites Integration beta'' plug-in? I desativated them, as I do not like having many addons in my browser, it slows it down. Is it okay?

---

### Post by whitesmith on 2014-04-29
> **Tar_Ni said:**
> Ok thanks a lot guys, I will sit and wait and see how it goes in the next few days to get prompted automatically. :)

Other question: What is the ''Ubuntu firefox modification'' and ''Unity websites Integration beta'' plug-in? I desativated them, as I do not like having many addons in my browser, it slows it down. Is it okay?Since you don't name all add-ons on your installation, who can say? What I would do is write a short script that times the interval between double-click and browser launch. Run it and save the result. Now go to Preferences->Privacy and check Always Use Private Browsing Mode. The latter disables all add-ons. Compare the two times. If there's a difference that matters to you, get granular and measure timings with each add-on separately. You need to be methodical if every millisecond matters. Yes, every add-on slows down things a bit, but at the price of functionality. Cheers.

---

### Post by jbaerboc on 2014-04-29
I have all my ubuntu plugins disabled in firefox and haven't seen a problem from it. I think it's designed to integrate it more into the ubuntu system but I honestly haven't really noticed a difference. Also you can always re-check them if you notice a change that bothers you. I do use FFox on ocassion but mostly use Chrome so it's possible I missed something that was indeed affected.

---

