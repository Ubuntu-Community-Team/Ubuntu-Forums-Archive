---
title: "Update Manager &quot;Check&quot; Box"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-06-05
Hi,    This is both a question and possible info for other beginners.  I'm now pretty familiar with Update Manager.  In Ubuntu 11.10 Unity, it jiggles in the side panel, I open it and see updates I can choose to install or not.  Mostly I install them, and all is well.

Recently I opened Update Manager, and decided to click the "Check" box, thinking it would check for regular updates.  Instead, it does something entirely different.  It checks for and installs updates to Sources and Cache and Packages.  This is sort of counter-intuitive.  Is this a function that should be "check"ed often?  Since it does this separate function, shouldn't it be labeled in a way that points this out?

And generally, are there other routine maintenance functions that I'm missing?

Thank you,  Blessed Ubuntu Gurus!

---

### Post by Frogs Hair on 2012-06-05
No guru in this skin.  
Selecting check for updates  connects to the sources and updates/ refreshes the package list. This is the same as running this terminal command. ```
sudo apt-get update
```

Selecting install updates is the same as this command ```
sudo apt-get upgrade
```

I check the update manager daily and like to run check for updates prior to installing software , but it is not required. When installing ppas the first command is used after adding a new source and before a package installation.

In the update manager > settings there are options as to when to check for and display  updates. I don't use the automatic options, but that is a matter of preference .

---

### Post by deadflowr on 2012-06-05
All clicking the "Check" box does is refresh what has been loaded in the repos, it checks the source, cache, and packages for newer updates for any packages you have. Clicking "Check" box does not install any program updates, it does not even download them. I click "Check" box all the time, as I frequently let updates sit in the update-manager queue for sometimes days at a time, clicking "Check" box brings my system current.
If for some reason, clicking "Check" box does start installing updates, this would mean that somehow the update-manager has been corrupted. But having run "Check" box quite often for close to two years, that has never happened to me.

---

