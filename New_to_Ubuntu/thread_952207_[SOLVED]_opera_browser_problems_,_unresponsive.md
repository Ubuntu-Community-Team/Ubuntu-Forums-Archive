---
title: "[SOLVED] opera browser problems , unresponsive"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-10-18
hi folks , my opera browser is really messing about at the moment its so bad its unusable.
i really like opera especially the fit to width as my eyesight isnt to good these days i view at 150% AND AT THIS SIZE THE FIT TO WIDTH REALlY HELPS. 
the problem i have is the mouse pointer keeps fliting about for no apparent reason , this really drives you round the bend,also i spend a lot of time browsing ebay and it really works incredibly slow on ebay , it keeps freezing up , and i have to force quit to be able to continue, i have also been having a problem shutting down my pc when things go wrong, it takes about 4 minutes or longer to shut down. so i decided to remove opera and the flash player .i did this and then reinstalled with the latest versions of booth, opera 9.6 and flash 10,its even worse now.i dont know what else to do to fix it ,i have noticed that when i open opera it says another one is still running or something and i have to click on still want to proceed to open opera , i cannot find another version running anywhere so dont know what this is about. 
i am lost without my favorite browser please could someone help me get it working again asap , i would be most grateful of any help given. thanks andrew

---

### Post by Coastal Confessions on 2008-10-18
Have you tried rebooting?

---

### Post by workshop1702 on 2008-10-19
yes no luck

---

### Post by mnmus on 2008-10-20
I've been having a similar problem with Opera 9.6 (build 2444). Funny thing, though, Opera 9.6 (build 10447) for Windows running under WINE on the same box has no such issues. 

I hate to take the uninstall/reinstall step with my Linux version of Opera, because a full uninstall means locating and scrubbing all the customizations--including custom keystroke combos, wand passwords, etc. Locating the files isn't the tough part, but rebuilding them (assuming something in the customizing I've done is at fault) is a tedious process. *sigh*

I don't think the customizations I've done are at fault though, since I have configured my Windows version (running under WINE) to use the Linux install's customization files (just changed the path statements in opera:config).

BUT, what you're running into when you invoke Opera and you're told another instance is running tells me you did not do a complete uninstallation of Opera. In the address bar, enter "opera:config" (W/O the "") and press "Enter". Go down to User Prefs and note the paths to the ini files. In either a terminal session or in your file browser, navigate to those files and nuke 'em after doing another uninstall. Then reinstall Opera and you'll likely at least do away with the error message.

But I still don't know if that'll fix the browser freezes. My guess is, probably not. I suspect a Flash problem, because mine ALWAYS freezes, now, when the flash plugin is invoked, although at other times I'm not sure there's flash running in one of my open tabs, so... 

I'm finally torqued enough that I'm heading over to try submitting a bug report with Opera.

----
AMD Athlon 64X2 5200+
4GiB RAM
64-bit Ubuntu 8.04, 2.6.24-21 kernel

---

### Post by Daveth on 2008-10-20
I have certainly noticed mutiple opera processes running sometimes- an alternative is to look in the system processes tool (under settings/admin) and look to the processes tab. You will sometimes see the cpu flat out running 2 opera processes. No idea why it does not close it. I usually use the kill command and the pid, with the -9 flag to kill 1 off.
I have just downloaded 9.6 and flash 10 and if anything it seems snappier and more responsive than the previous incarnations, so not idea what is happening on your systems!

---

### Post by workshop1702 on 2008-10-23
thanks for all the help, appears that there are two operapluginwraper both running seem to be something to do with the flash player, should there be two they appear to be slightly different as the details when i put my pointer on each is different, should i have two,there only appears to be one opera running.
its such an annoying problem as sometimes opera flies and then all of a suden it crawls, my gut fealing is its something to do with the flash player, affraid i am not enough of an expert to know how to cure it.i am learning thanks to all of the help but have a long way to go. any more help would be appreciated. Thanks Andrew

---

### Post by workshop1702 on 2008-10-23
affraid i cannot get this the suggestion of entering "opera:config" (W/O the "") in the address bar, presumably you mean the opera address bar, what should i enter exactly please? or does anyone else have any ideas how i can find and remove any left over files from the previous version i had installed.thanks agin for the help. andrew

---

### Post by Daveth on 2008-10-29
are you having the same problems with version 9.61???

---

### Post by workshop1702 on 2008-10-29
didnt know there was a 9.61 , just installed it and it seems a lot more responsive so far. lets hope it stays that way . thanks for the suggestion. Andrew

---

### Post by workshop1702 on 2008-11-05
its still not wright seems to run very slow at times real pain in the backside ,still need help please.:confused:

---

