---
title: "Gui software updater vs. terminal."
date: 2013-11-29
forum: New to Ubuntu
---

### Post by thatredbird on 2013-11-29
I have been using the gui software updater in Lubuntu, around once a day, usualy there are just small tweaks it seams, but today there was around 40 mb of updates.  Is this  a fairly common thing with Lubuntu?  My other question was is the graphical interface the best way, or is there a terminal option that would be more efficient/recomended

---

### Post by fantab on 2013-11-29
Yeah those updates are normal, updates and fixes are release as they come, sometimes updates will be less in size and sometimes more...
GUI Software Updater does the same job as the Terminal. What software updater do you have? Install 'synaptic' package manager, if you don't have it already. IMO it handles the updates/upgrades, installing/uninstalling packages better.

From Terminal you can use:
```
sudo apt-get update && sudo apt-get upgrade
```

To install packages:
```
sudo apt-get install packagename
```

---

### Post by thatredbird on 2013-11-30
Thanks so much for the fast reply, I will try that way. I believe the manager I was using was the default in lubuntu.

---

### Post by oldos2er on 2013-11-30
> **thatredbird said:**
> I have been using the gui software updater in Lubuntu, around once a day, usualy there are just small tweaks it seams, but today there was around 40 mb of updates.  Is this  a fairly common thing with Lubuntu?  My other question was is the graphical interface the best way, or is there a terminal option that would be more efficient/recomended

I have an alias in my ~/.bashrc: ```
alias up='sudo apt-get update && sudo apt-get dist-upgrade'
``` so I just type *up* in terminal, enter my password, and I'm done. Very efficient.

Either method you use, terminal or GUI update manager, is really down to personal preference. They're both just interfaces to the APT system.

---

