---
title: "Keeping Ubuntu Clean"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by ryanparrish on 2008-06-12
Hello, 

I am wondering as to how do I keep Ubuntu clean and running at peak performance?

---

### Post by sdennie on 2008-06-12
The easiest way to keep it "clean" is to only install applications via "apt-get" or "Synaptic Package Manager" and only from trusted sources.

As for performance, Ubuntu runs fairly well without any user intervention.  There are tweaks but I can't recommend them unless you fully understand what they are going to do and what the risks are.  If you feel some part of your system isn't running as fast as you think it should, then sure, see if you can find a way to make it "go faster" but, otherwise, I wouldn't try to fix it until you are sure that it's broken.

---

### Post by forger on 2008-06-12
1) watch what you install
2) you might want to clean the temporary backup files that gedit leaves while you edit (text) files.
> find /home/ -depth -name "*~"

You can rmeove them all with this command:
> rm -i `find $HOME -depth -name "*~"`
3) when you remove packages, use apt-get purge or aptitude purge or complete removal in synaptic
4) check your disk periodically (once a month) with smartctl:
[http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With](http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With)
Also use the e2fsck command to check them again once every month.

---

### Post by cprofitt on 2008-06-12
My recommendation would be to install deborphan

```

sudo apt-get install deborphan

```Then you can create a custom filter in Synaptic Package Manager that will show you orphans... from there you can decide to remove (uninstall) them or not.

---

### Post by wolfen69 on 2008-06-12
a couple things you can do:
```
sudo apt-get clean
``` 
```
sudo apt-get autoremove
``` removes any unused packages.

---

### Post by ryanparrish on 2008-06-12
thank you all I will give them a shot :)  Also I got to remember to not yell at my computer to go faster when I am running virtual box in seamless mode and I am running Gimp and Open office all at once on a 1.73 dual core with a gig of ram sure cant due that with vista crash before it even got there thanks again

---

### Post by Xiong Chiamiov on 2008-06-13
> **forger said:**
> 
2) you might want to clean the temporary backup files that gedit leaves while you edit (text) files.

You can turn that behavior off somewhere in gedit's preferences if it annoys you, as it does me.

---

### Post by forger on 2008-06-14
> **Xiong Chiamiov said:**
> You can turn that behavior off somewhere in gedit's preferences if it annoys you, as it does me.

I actually love the way it backs up the file :)

---

### Post by akiratheoni on 2008-06-14
Kind of off-topic but you can also install preload.

```
sudo apt-get install preload
```

What it does is that it learns what applications you use the most and loads them into memory first so applications load them up faster. It doesn't exactly keep Ubuntu clean but everyone else suggested solutions for that matter so mine just helps performance :P

---

