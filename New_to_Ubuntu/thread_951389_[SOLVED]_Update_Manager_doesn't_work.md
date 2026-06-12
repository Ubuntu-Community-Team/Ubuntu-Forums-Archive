---
title: "[SOLVED] Update Manager doesn't work"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by brucenduane on 2008-10-18
I have Ubuntu 8.04.1 installed on Toshiba Laptop

Update Manager says there are 63 packages to update.
I press the Install Updates button and nothing happens, I just refreshes the list.

The first item is cupsys Version 1.3.7-1ubuntu3.1

When I go to Synaptic Package Manager and reload the latest package
is lists for cupsys Version 1.3.7-1ubuntu3  Note: not 3.1

I have run the following:
sudo apt-get update
sudo aptitude update
plus ran RELOAD in Synaptic Package Manager
I have tried both the England and US repositories.

Still Update Manager wants to install packages that are newer than
what the system knows about.  What is going on???

I do have the package "apt-mark-sync" installed

What should I do next??

Ryadt:  This is the same system that had the screen resolution problem.
Does this mean the system is corrupted and needs to be re-installed???

Thanks for the help.

---

### Post by eternalnewbee on 2008-10-18
> **brucenduane said:**
> I have Ubuntu 8.04.1 installed on Toshiba Laptop

Update Manager says there are 63 packages to update.
I press the Install Updates button and nothing happens, I just refreshes the list.

The first item is cupsys Version 1.3.7-1ubuntu3.1

When I go to Synaptic Package Manager and reload the latest package
is lists for cupsys Version 1.3.7-1ubuntu3  Note: not 3.1

I have run the following:
sudo apt-get update
sudo aptitude update
plus ran RELOAD in Synaptic Package Manager
I have tried both the England and US repositories.

Still Update Manager wants to install packages that are newer than
what the system knows about.  What is going on???

I do have the package "apt-mark-sync" installed

What should I do next??

Ryadt:  This is the same system that had the screen resolution problem.
Does this mean the system is corrupted and needs to be re-installed???

Thanks for the help.

Hi there.
Have you tried downloading from the main server?

---

### Post by brucenduane on 2008-10-18
I check the setting in the Synaptic Packager Manager Preferences
and I had set the preference for the current package.

When I changed this to the Latest Package, Synaptic Package Manager
found the latest and is installing the 63 packages as I type.

This is solved.

---

### Post by eternalnewbee on 2008-10-18
> **brucenduane said:**
> I check the setting in the Synaptic Packager Manager Preferences
and I had set the preference for the current package.

When I changed this to the Latest Package, Synaptic Package Manager
found the latest and is installing the 63 packages as I type.

This is solved.

...And may the Ubuntu force be with you...
This is the way to go, through trial & error, patience, and the Ubuntu Forums.
Good luck.

---

