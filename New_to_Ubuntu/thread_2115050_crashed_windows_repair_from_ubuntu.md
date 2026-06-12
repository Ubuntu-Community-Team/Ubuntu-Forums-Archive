---
title: "crashed windows: repair from ubuntu?"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by Lalaith on 2013-02-11
Hello!

I'm using a dual boot laptop, using Windows for gaming and Ubuntu for all the rest. 

After installing a new program in windows, everytime I tried to launch windows it took ages to boot up (always going through a recovery/repair process before starting normally). I tried to repair the problem but I just made it worse (as I said, the important things were running under ubuntu, so I dind't do it with care...) and now I cannot boot windows, neither in safe mode. 

I would like to know:

- if the problem was caused by a driver (as I suspect it is), is there any chance that I can repair it through ubuntu? (I must say I'm not experiencing any problems in ubuntu)

since I don't know much about computers and don't want to end up throwing my laptop to the trash, I thought that the easiest way would be to make a clean install of windows. But I read that it's quite difficult to install windows next to another OS, and that the best way is to clear everything, install win and ubuntu afterwards.  So my second question is:

- how can I uninstall the whole Ubuntu and delete the partition I did for it, so that I can reinstall windows without troubles?

as a side note, my laptop doesn't have any CD-rom device, so the recovery filesfor windows are not on a CD, but on another partition of the laptop...

Any help, either in form of answer or links to other resources, will be much appreciated :)

---

### Post by stoogiebuncho on 2013-02-11
1)  What was the program you installed that caused the problem with Windows?  It sounds like something was preventing Windows from shutting down properly.

2) What did you do when you tried to repair the problem?

3) I don't think it's possible to say if this is a driver problem or not based on the information you've provided.  Did you recently update a driver?

4) You can install Windows alongside of Ubuntu, without wiping Ubuntu first.  Just make sure you know which partition you are installing Windows to, and go through the whole process.  When that's done, you will have to boot a live CD or live USB and reinstall grub.  There are a lot of sites that walk you through this process - I've done it myself and it's pretty easy.

---

### Post by Lalaith on 2013-02-12
Hi, 

so the whole story is:

After installing a game named World of Tanks, Windows needed a repair each time I started it. Browsing a bit on the web, I read that one of the solutions was to make sure that Windows was updated. I downloaded and installed the updates, and afterwards windows wasn't able to boot, and in safe mode neither.
At that time I read other solutions but I had to choose one... and failed. 
I will try to reinstall windows then, without touching ubuntu... do you have any useful tip?

---

### Post by Mark Phelps on 2013-02-12
Are you running Windows 7? If you were, then you should go to the Win7 forums (sevenforums.com) as they have some tutorials for doing reinstalls WITHOUT removing your current stuff.  It's complicated and needs installation media -- but I've done it, and it works.  

If you have to erase and reinstall Win7, you should think seriously about copying off files you need to save from Ubuntu before you do that.

---

