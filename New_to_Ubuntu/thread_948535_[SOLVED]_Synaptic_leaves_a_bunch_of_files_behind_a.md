---
title: "[SOLVED] Synaptic leaves a bunch of files behind after removing a program"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by susanne260 on 2008-10-15
Using Synaptic, I installed a game called Xmoto, and later decided to remove it with the "complete removal" (remove with configuration) option. But after I searched the filesystem for "xmoto", this is what I got: [http://snipurl.com/4duns](http://snipurl.com/4duns)

About 20.3MB of files. Is it safe to remove all of them? Is there are a reason why they weren't removed, even though I chose the "complete removal" option in Synaptic?

I'd like to install and try out a very large number of different programs with Synaptic, but if every one of them starts leaving behind dozens of megabytes of data, I think I might soon run out of diskpace. :p

---

### Post by mikeize on 2008-10-15
Those are safe to remove.  I don't know why 'complete removal' leaves them behind, but you can try (in terminal) 'apt-get autoremove' (no quote marks).  Also, maybe you can look in the left pane of synaptic for the filter "not installed residual config", where you can (very tediously) mark each item for complete removal.

---

### Post by Therion on 2008-10-15
Install [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11).  It'll keep things squeaky clean.  

It has a whole host of other things it can do as well.  Very handy!!

Be sure to read the install instructions... Very simple but not your typical .deb install.

---

### Post by Nepherte on 2008-10-15
It's completely safe to remove them manually. Typically when you remove an application, the settings of the program remain (/home/susanne/.xmoto). That way you will keep the application's settings when you reinstall it. When you don't want to keep these settings when you remove a program, you can purge them:
```
sudo apt-get purge applicationname
```

When you install a program, the deb package is first placed into /var/cache/apt/archives and installed afterwards. The deb file remains there in case you want to reinstall the program. That way you don't have to download it again before installing. You can remove this cache with:
```
sudo apt-get clean
```

---

### Post by susanne260 on 2008-10-15
> **mikeize said:**
> ... but you can try (in terminal) 'apt-get autoremove' (no quote marks).  Also, maybe you can look in the left pane of synaptic for the filter "not installed residual config", where you can (very tediously) mark each item for complete removal.

Yes, Synaptic removed unneeded dependencies, so "sudo apt-get autoremove" just displayed that there were no unneeded dependencies to remove. And yes, there were some entires under  "not installed residual config" in Synaptic, so I removed them, however they didn't seem to remove any files in this case.

> **Therion said:**
> Install [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11).  It'll keep things squeaky clean.

Thanks for the suggestion, I might give it a try later. Although I'll first try to get used to using Synaptic and apt-get before trying any other not so common ones. :p

> **Nepherte said:**
> It's completely safe to remove them manually. Typically when you remove an application, the settings of the program remain (/home/susanne/.xmoto). That way you will keep the application's settings when you reinstall it. When you don't want to keep these settings when you remove a program, you can purge them:
```
sudo apt-get purge applicationname
```


Well, maybe that command did remove the configuration folder (/home/username/.application) in the earlier versions of Ubuntu. But in Ubuntu 8.04 the command "sudo apt-get purge applicationname" seems to leave the configuration folder intact... at least in my case.

I read the manual page that I have to add the "--auto-remove" parameter to that command, in order for it to also remove the unneeded dependencies as well. So I don't need to run "apt-get autoremove" later to clear up the mess.


> **Nepherte said:**
> When you install a program, the deb package is first placed into /var/cache/apt/archives and installed afterwards. The deb file remains there in case you want to reinstall the program. That way you don't have to download it again before installing. You can remove this cache with:
```
sudo apt-get clean
```

That cleared up a whole bunch of big unneeded package files, thanks! I also discovered that if I select the "Delete downloaded packages after installation" in [Settings] - [Preferences] - [Files tab] in Synaptic, it doesn't leave the big package files on the drive after installing a package, so that spares me of doing "apt-get clean" every now and then. :p


Well, in conclusion I kind of got the problem solved. Well, not completely, as I still have to delete the programs' configuration folders in /home, and programs also leave behind small 5-20KB files in */usr/share* and other folders, but those don't bother me, as they aren't big enough to become an issue. :D

---

