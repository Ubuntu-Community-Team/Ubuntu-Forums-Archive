---
title: "Junk files/invalid registry etc!"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-16
Hi guys
 
I used to use CC Cleaner in Windows to Clean up junk files and invalid Registry entries etc - do I need to do the same in Ubuntu?
 
Regards
 
Clive

---

### Post by Double.J on 2012-01-16
It isn't really as much of a problem in ubuntu to be honest. However if you keep adding and removing packages.. especially as a new user you may build up a bunch of dependencies you don't really need!

To get rid of these, just run the following command in the terminal:
```

sudo apt-get autoclean

```


The other left over bits you may get are config files - especially if you remove packages with remove instead of purge. Easy way to get rid of these - run synaptic and go residual config>mark for deletion. 

Hope it helps :)

---

### Post by cliveT on 2012-01-16
Ok thanks, I`ll try that if I need to.

---

### Post by cliveT on 2012-01-18
> **gnu/mirow said:**
> It isn't really as much of a problem in ubuntu to be honest. However if you keep adding and removing packages.. especially as a new user you may build up a bunch of dependencies you don't really need!

To get rid of these, just run the following command in the terminal:
```

sudo apt-get autoclean

```
The other left over bits you may get are config files - especially if you remove packages with remove instead of purge. Easy way to get rid of these - run synaptic and go residual config>mark for deletion. 

Hope it helps :)

I can`t find "residual config" in Synaptic?

Using 11.10

---

### Post by Paqman on 2012-01-18
If you really want to give your system a good scrape out install [bleachbit]("apt:bleachbit"), although tbh it's more people who are a bit fussy about tidiness. It won't really make your system run any better. I give it a run through once or twice a year to clear out old caches and such.

---

### Post by mcduck on 2012-01-18
> **cliveT said:**
> I can`t find "residual config" in Synaptic?

Using 11.10

Select "Status" from the buttons in the bottom left corner, and the filter list on the left side shows things like "Installed", "Installed(local or obsolete" etc. The "Not Installed (residual config)" filter will appear there if you have such packages.

...also keep in mind that the package manager will never touch the user-specific configuration files in your home directory. If you want to remove those as well, you'll have to do it manually. On the other hand they are just very small text files, and will not use any noticeable amount of disc space or slow down your computer in any way. So pretty much the only reason you'd need to remove any such file would be if you were having problems with a specific program and wanted to reset it to default settings.

In general maintaining a Linux system takes very little effort. Install updates when they become available, keep regular backups of your important files, and run "sudo apt-get clean" every now and then, depending how much disc space you have. Linux systems don't gather much junk, as the package management is very effective in handling all the files and there is no registry like in Windows. All the temporary files get removed automatically, and even the few config files left around if you use the basic uninstall option will not slow your system down in any way.

---

### Post by cliveT on 2012-01-18
mcduck -thanks for that and to all you guys, I now understand it.

regards

Clive

---

### Post by Paqman on 2012-01-18
> **mcduck said:**
> 
In general maintaining a Linux system takes very little effort. 


This

> 
run "sudo apt-get clean" every now and then

Bear in mind this will dump your whole APT cache. If you just want to dump the obsolete files, use autoclean instead of clean.

---

### Post by mcduck on 2012-01-18
> **Paqman said:**
> 
Bear in mind this will dump your whole APT cache. If you just want to dump the obsolete files, use autoclean instead of clean.

True. I suppose which one works better for you depends on how often you actually need to reinstall packages.

"apt-get clean" will free you a lot more space, but if you want to reinstall a package it needs to be downloaded from the repositories.

"apt-get autoclean" will only remove .deb files of the packages you don't even have installed any more, which makes the amount of freed space a lot smaller and leaves you with lots of cached files you probably will never need, but if you often need to reinstall packages and you have slow Internet connection this might be better option than a full "clean".

---

### Post by Paqman on 2012-01-18
> **mcduck said:**
> 
"apt-get autoclean" will only remove .deb files of the packages you don't even have installed any more

It also dumps packages which have a newer version available in the repos. Effectively it ditches everything that you would never use to reinstall a package.

Like you say, which one you prefer just depends on how much disk space you need to free up.

---

