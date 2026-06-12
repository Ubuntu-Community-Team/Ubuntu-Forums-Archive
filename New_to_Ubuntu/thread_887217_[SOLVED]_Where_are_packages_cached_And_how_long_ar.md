---
title: "[SOLVED] Where are packages cached? And how long are they kept?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by t0p on 2008-08-11
I've noticed that if I uninstall a package, then later decide to reinstall it, very often the package manager doesn't need to download it - the package has been cached locally, even though I have uninstalled it. So where are these packages being kept? And for how long? How much memory is being used keeping uninstalled packages? Can i free up memory by manually deleting these packages?

---

### Post by mc4100 on 2008-08-11
Don't know how long they're kept... but they're at:
```
/var/cache/apt/archives
```
You don't really need to worry about the space though, as you can remove them with:
```
sudo apt-get clean
```
or the 'intelligent' version
```
sudo apt-get autoclean
```

---

### Post by tech0007 on 2008-08-11
> **t0p said:**
> I've noticed that if I uninstall a package, then later decide to reinstall it, very often the package manager doesn't need to download it - the package has been cached locally, even though I have uninstalled it. So where are these packages being kept? And for how long? How much memory is being used keeping uninstalled packages? Can i free up memory by manually deleting these packages?

The debs are in /var/cache/apt/archives.  You can save hard drive space by running 'sudo apt-get clean'.  This will delete the debs which you already installed.

---

### Post by iaculallad on 2008-08-11
Cached packages are installed at this directory:

> /var/cache/apt/archives

And, they are stored their as long as you want unless you want them deleted. To clean your cache, issue the command:

```
sudo apt-get clean
```

---

### Post by Vivaldi Gloria on 2008-08-12
> where are these packages being kept? 

```
/var/cache/apt/archives 
```

> And for how long? 

Configured in 

```
/etc/apt/apt.conf.d/20archive
```

> How much memory is being used keeping uninstalled packages? Can i free up memory by manually deleting these packages?

No memory used what so ever. Do you mean disk space?

---

### Post by t0p on 2008-08-12
Thanks, all! And yes, vivaldi, I did mean disk space.

---

### Post by LinoX on 2008-12-19
..and how can I tell apt-get to cache every package locally?
I don't have an internet connection at home and I don't want to be stuck when I try to install the packages I need (for example smbfs)

Thank you.

---

### Post by gTinker on 2008-12-19
> **LinoX said:**
> ..and how can I tell apt-get to cache every package locally?

That is the default behaviour for apt-get.

[edit] After looking at what you wrote again, I think I might have misunderstood. It's default to keep installed packages in the cache. Do you mean you want all the binaries in all repositories stored locally? Do you have disk space for that? Maybe you want something like apt-mirror.

---

### Post by LinoX on 2008-12-22
YESSSSSSS!!!! :KS
THANK YOU VERY MUCH!!

It's what I was looking for :)

---

