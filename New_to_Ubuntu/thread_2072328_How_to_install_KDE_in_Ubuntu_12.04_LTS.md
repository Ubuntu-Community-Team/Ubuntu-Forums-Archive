---
title: "How to install KDE in Ubuntu 12.04 LTS?"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by boomz on 2012-10-17
Recently I became curios with Linux's desktop environment, I have stumbled with Unity and Gnome. The next one I want to try is KDE, but I can't find any help from Google, maybe there is an answer from the forum. :) Thank you so much! :)

---

### Post by Cheesemill on 2012-10-17
You can install KDE and all of its default apps by simply doing:
```
sudo apt-get install kubuntu-desktop
```Then just select KDE as your session from the login screen.


If you just want the KDE desktop without any of its default applications you can do this instead:

```
sudo apt-get install kubuntu-desktop --no-install-recommends
```

---

### Post by thewolfman on 2012-10-17
Hi,

if you want to try KDE, open Synaptic and search for kubuntu-full, this will install the full version of the current KDE desktop, you can add to it afterwards, you must select the "KDM" (KDE desktop manager at the login window by clicking on the little cogwheel and selecting KDE, then login in to your new desktop, you can change it any time at the login window.

You can also install the same using a terminal command:

**sudo apt-get update && sudo apt-get install kubuntu-full**

Regards thewolfman:P

---

### Post by boomz on 2012-10-17
Thank you for the efforts sir **Cheesemill** and **thewolfman**, but i have this message after entering the code on the terminal

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


How can I resolve this? Thank you very much! :)

---

### Post by offgridguy on 2012-10-17
I recently had a thread of my own called - unity or kde?,      There was a lot of useful input there
if you wanted to check it out.

---

### Post by boomz on 2012-10-17
Thank you so much! :)

---

### Post by audiomick on 2012-10-17
> **boomz said:**
> ... i have this message after entering the code on the terminal...How can I resolve this? Thank you very much! :)

Firstly, did you, for instance, have the software centre open when you used an "apt-get" command?

This
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 

is what makes me ask that. You can't have two things going that both use the package manager back end. Even have the update manager in the background waiting for you to notice it when you try an install something can give you a problem, I believe. So, one thing at a time.

The missing key is for the medibuntu PPA. You must have added that at some point. If that message persists, you might want to re-install the PPA and key. It might be possible to just go and get the key again, but I don't know how. I would just go to synaptic or the software centre and remove it, then go here
[http://www.medibuntu.org/repository.php]("http://www.medibuntu.org/repository.php")
and get it again.

---

