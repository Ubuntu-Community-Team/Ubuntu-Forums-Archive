---
title: "[SOLVED] sudo apt-get update/upgrade"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-10
what is the difference between an update, and an upgrade?
It seems like the icon for updates available offers different updates than the CLI command because after updating/upgrading from the CLI the icon remains in the top panel.  Is this right or am I seeing things?

---

### Post by tamoneya on 2008-07-10
update: check repositories for new packages or updated packages
upgrade: get any new/upgraded packages and install them

---

### Post by snowpine on 2008-07-10
> **adamogardner said:**
> what is the difference between an update, and an upgrade?
It seems like the icon for updates available offers different updates than the CLI command because after updating/upgrading from the CLI the icon remains in the top panel.  Is this right or am I seeing things?

'update' checks your software sources for a fresh list of what's available.

'upgrade' actually downloads and installs the available updates.

---

### Post by avtolle on 2008-07-10
Yes, the icon remains on the top panel; grayed out while the package manager does some "behind the scenes" work after installing the updates (it will go away after the package manager is done); or, if there is, e.g., a new kernel, it will remain "lit up" until the new kernel is installed. To do this from the CLI, do ```
sudo apt-get update && sudo apt-get dist-upgrade
```which will d/l and install those things kernel (and a few other things I don't currently know) related, at which time the icon will gray out, etc.

---

### Post by rolnics on 2008-07-10
> **adamogardner said:**
> 
It seems like the icon for updates available offers different updates than the CLI command because after updating/upgrading from the CLI the icon remains in the top panel.  Is this right or am I seeing things?

Or are you meaning, like me I'm starting to use CLI to get updates, but sometimes when i do apt-get holds back on some updates, but those same updates are processed via the update manager icon? Or is that just some weird issue i'm having?

---

### Post by avtolle on 2008-07-10
> **rolnics said:**
> Or are you meaning, like me I'm starting to use CLI to get updates, but sometimes when i do apt-get holds back on some updates, but those same updates are processed via the update manager icon? Or is that just some weird issue i'm having?
Not a wierd issue you are having; as I posted above, sometimes the held back updates need to be installed from the CLI using sudo apt-get dist-upgrade, which is why using the update manager icon will install them. In certain other cases, there are dependencies needed to install the new package but the dependencies are not yet upgraded, in which case neither the CLI nor the update manager icon will download them.

---

### Post by adamogardner on 2008-07-10
ok so what I'm hearing is that after I do update, then I do up grade because the latter activates the former?
I also am hearing that on occasion a new and improved kernal comes out with or without warning except that the icon remains, and to remedy this icon I input: sudo apt-get update && sudo apt-get dist-upgrade.

---

### Post by avtolle on 2008-07-10
When you do the update command, the information in the system as to the repositories is refreshed "to date". When you do the upgrade command, the refreshed information is used by the system to determine whether there are updated packages to install to update your system, and, if so, the same are reported to you and then, after you accept them, downloaded and installed. During this process, some packages will be "held back" for the reasons I posted earlier. To install updated kernel, the dist-upgrade command is used. Many recommend that when doing a CLI update, all three commands be used, e.g.```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```to get all available updates installed. HTH.

---

### Post by adamogardner on 2008-07-10
thankyou 4 clarifying

---

### Post by rolnics on 2008-07-13
thanks avtolle, for explaining that one, just had my weird issue, but with your explanation it's not an issue now, just another thing i've learnt about linux!

---

