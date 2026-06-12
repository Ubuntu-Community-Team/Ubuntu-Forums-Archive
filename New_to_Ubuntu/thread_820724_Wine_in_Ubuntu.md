---
title: "Wine in Ubuntu"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by wbrokow1 on 2008-06-06
I tried search for Wine in the package install section of Ubuntu, but it was not there.  I am using version 8.04 by the way.
Is there a way to install Wine.

Thanks for any help

---

### Post by yurikoster1 on 2008-06-06
hello m8
try this command

sudo apt-get update && sudo apt-get install wine

its wot i used in my own hardy

---

### Post by DM was on fire! on 2008-06-06
I don't think Wine is added to the sources list in Hardy.

Type the following into Terminal:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get upgrade && sudo apt-get install wine
```

---

### Post by yurikoster1 on 2008-06-06
> **yurikoster1 said:**
> hello m8
try this command

sudo apt-get update && sudo apt-get install wine

its wot i used in my own hardy

if if doesnt work try check all repositories in

System> Administration > Synaptic package manager

stteings menu on the top repositories

---

### Post by Oldsoldier2003 on 2008-06-06
> **DM was on fire! said:**
> I don't think Wine is added to the sources list in Hardy.

Type the following into Terminal:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get upgrade && sudo apt-get install wine
```

Wine is indeed in the Hardy repos. The Hardy repos were locked at release so wine in pinned at version 0.9.59.

---

### Post by DM was on fire! on 2008-06-06
> **Oldsoldier2003 said:**
> Wine is indeed in the Hardy repos. The Hardy repos were locked at release so wine in pinned at version 0.9.59.

Oh.
Oops. ^^;;

---

### Post by Duck2006 on 2008-06-06
Any thing you want to load look in Synaptic Package Manager first.

---

### Post by stchman on 2008-06-06
> **wbrokow1 said:**
> I tried search for Wine in the package install section of Ubuntu, but it was not there.  I am using version 8.04 by the way.
Is there a way to install Wine.

Thanks for any help

WINE has been in the repos since Gutsy.  Make sure you have the main, universe, multiverse, and restricted repos enabled.

---

