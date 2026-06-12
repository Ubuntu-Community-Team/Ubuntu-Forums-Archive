---
title: "Auto Update"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Kracer on 2011-10-14
Somehow in my 11.04 installation I made all my programms update automatically.
During the upgrade it told that it was turned off.
how do I turn it back on?
Thanks in advance

---

### Post by kolinab on 2011-10-14
In the dash, search for 'update manager.'

Start the update manager, and click 'settings' in the bottom left corner.

On the 'updates' tab you will find the information regarding update frequency and a few other options. 

Let us know if you get it working!

K

---

### Post by Kracer on 2011-10-15
I remember doing something in the package manager or that's something else?
So everything is being updated including non-conical supported software with the trick you sent me?

---

### Post by kolinab on 2011-10-15
The package manager and the update manager are related but not exactly the same. You can open the package manager by searching for 'synaptic'. 

As far as what gets updated, if you have enabled the Canonical 'partner' repositories (look for the 'other software' and 'ubuntu software' tabs in the update manager settings. This is the same screen you can bring up through synaptic.

The software that is supported through those canonical repositories will be updated using the update manager. If you have installed OTHER software though, from sources other than the canonical or partner/multiverse repositories, it won't be updated through update manager.

Does that help?

---

### Post by Kracer on 2011-10-15
I get it.
But what is updated and what isn't?
I assume major programms like libre office, chromium, skype, wine etc. wil be updated.
What about drivers?
I know I'm a bit picky but i want to be up to date and know what is happening inside my machine.

---

### Post by kolinab on 2011-10-15
I'm picky too. So, if you run the graphical updater (the one that pops up telling you what packages are available for update), it will show you a list of packages that have newer versions and that you may choose to update. You can go down the list of checkboxes and deselect any packages you want, and they won't be updated. 

If you want more information about the details of the update of each package, you can click on the item in the list, and in the bottom part of the window should be some notes about the particular changes in that package. If you're picky then you can decide (or not) to update those packages.

I guess the answer is that drivers are update too. But like I say you can look at each item in the update list and see the details. 

I'm sorry I can't give you a more detailed answer - honestly I always apply all the updates. There was a time or two long ago when I was having a particular problem with some program and I chose to leave well enough alone but these days, especially regarding security updates, I just install them all.

You might find more useful information here, a website I recently found: [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)

Am I helping? :)

---

### Post by mcduck on 2011-10-15
> **Kracer said:**
> I get it.
But what is updated and what isn't?
I assume major programms like libre office, chromium, skype, wine etc. wil be updated.
What about drivers?
I know I'm a bit picky but i want to be up to date and know what is happening inside my machine.

All packages installed through the package management will be updated (if there are updates available, keep in mind that Ubuntu's policy for updates is that they are only provided after the release for security reasons and to fix serious bugs. Never just to give you the latest version of a program or new features).

Anyway, based on the question you asked, perhaps you enabled some PPA repositories or other third-party repositories in the previous Ubuntu version to get more up-to-date packages than what's available in Ubuntu's official repositories? In that case you'll just have to add such repositories again, they are always disabled during release upgrades as there is no guarantee that a third-party repository actually is available for the new release version, or any way to make sure packages from such repositories wouldn't conflict with ones from the new releases official repositories.

---

### Post by Kracer on 2011-10-15
Hmmm
So all the programms are updated and if I leave it on automatic i just don't worry about anything.

---

