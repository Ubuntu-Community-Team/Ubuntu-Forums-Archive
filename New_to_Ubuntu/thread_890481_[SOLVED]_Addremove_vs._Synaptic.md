---
title: "[SOLVED] Add/remove vs. Synaptic"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
Will I get the same software if I do a search through add/remove and synaptic? If not, how do I know which one to use if I'm looking for a certain software? And, however dumb this may sound: Is one "better" than the other? In what context?

---

### Post by Crafty Kisses on 2008-08-15
> **zzzonked said:**
> Will I get the same software if I do a search through add/remove and synaptic? If not, how do I know which one to use if I'm looking for a certain software? And, however dumb this may sound: Is one "better" than the other? In what context?

I'm pretty sure there is a wider selection in Synaptic, please correct me if I'm wrong, I tested it myself some packages don't come up on Add/Remove, but I'm pretty sure Synaptic shows a lot more packages.

---

### Post by iaculallad on 2008-08-15
*Add/Remove option = This gives you the basic packages that comes with the distribution CD/DVD for installation.
*Package Manager = This gives you a broader lists of packages as it includes different repositories for package download.

EDIT: An alternative for (Synaptics) Package Manager would be:

```
sudo apt-get install package_name
```

and 

```
sudo aptitude install package name
```

---

### Post by Crafty Kisses on 2008-08-15
> **iaculallad said:**
> *Add/Remove option = This gives you the basic packages that comes with the distribution CD/DVD for installation.
*Package Manager = This gives you a broader lists of packages as it includes different repositories for package download.

That's a good way of putting it, iaculallad. :)

---

### Post by Elfy on 2008-08-15
I think that add/remove shows less than synaptic - a search for intel in add/remove gives 19 hits, synaptic many more than that.

If you know what you are looking for then synaptic is better - it might not be in add/remove - consequently you might think you can't install something - if you'r enot sure google first then check either synaptic or you can use the terminal to search

```
apt-cache search package
```

For the amount of software in synaptic - check my sig :D

---

### Post by abcuser on 2008-08-15
Hi,
Add/Remove for new users to make install as easy as possible.
Synaptic for advanced users to install any package that is not already in Add/Remove.
Regards,
Abcuser

---

### Post by abcuser on 2008-08-15
> **iaculallad said:**
> 
```
sudo apt-get package_name
```

sudo apt-get **install** package_name

---

### Post by iaculallad on 2008-08-15
> **abcuser said:**
> sudo apt-get **install** package_name

Haste makes Waste as they say :) Corrected it

---

### Post by billgoldberg on 2008-08-15
> **iaculallad said:**
> *Add/Remove option = This gives you the basic packages that comes with the distribution CD/DVD for installation.
*Package Manager = This gives you a broader lists of packages as it includes different repositories for package download.

EDIT: An alternative for (Synaptics) Package Manager would be:

```
sudo apt-get install package_name
```

and 

```
sudo aptitude install package name
```

Nice, but not entirely true.

I'm pretty sure that when you add a repo, some packages should show up in Add/Remove.

Unless I'm wrong, haven't used it in ages.

---

