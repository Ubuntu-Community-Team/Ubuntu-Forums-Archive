---
title: "Installing Backtrack5 tools + menu in Ubuntu 10.10"
date: 2011-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Zvlwab on 2011-11-17
I have had some trouble installing Backtrack5 tools and especially the menu in Ubuntu 10.10, so I decided to make a really quick guide for this.

1. Adding the repositories
Start Synaptic Package Manager
go to Settings -> Repositories -> Other Software Sources

Add these to your repository list.
 deb [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution main microverse non-free testing  
deb [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution main microverse non-free testing (only for 32-bit Ubuntu)
   deb [http://64.repository.backtrack-linux.org](http://64.repository.backtrack-linux.org) revolution main microverse non-free testing (only for 64-bit Ubuntu)
deb [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution main microverse non-free testing

Uncheck or remove (they are useless anyway) the newly added backtrack source repositories from the list.

Open up a terminal and run
```
you@computer:~$ wget -q [http://all.repository.backtrack-linux.org/backtrack.gpg](http://all.repository.backtrack-linux.org/backtrack.gpg) -O- | sudo apt-key add - 
you@computer:~$ sudo apt-get update && sudo apt-get upgrade
```You will already upgrade a couple of packages installed on Ubuntu to the ones in the Backtrack repositories.

2. Setting up the backtrack menu
IGNORE ANYTHING YOU HAVE GOOGLED ABOUT THIS BEFORE
```
you@computer:~$ sudo apt-get install backtrack-gnome-essentials backtrack-menu-icons
you@computer:~$ killall -9 gnome-panel
```backtrack-gnome-essentials installs the backtrack menu to your Gnome menu and backtrack-menu-icons installs the icons for the backtrack applications.
you need to kill the gnome panel to see the new icons instead of the "icon not found"-icons

I'm still looking for a way to see the backtrack menu specific icons, so if you find out how to see those, please post here. :)

I did this in Ubuntu 10.10 64-bit, but I guess it works for other Ubuntu versions using Gnome2 as well.

---

### Post by m3hdx on 2012-06-12
> **Zvlwab said:**
> I have had some trouble installing Backtrack5 tools and especially the menu in Ubuntu 10.10, so I decided to make a really quick guide for this.

1. Adding the repositories
Start Synaptic Package Manager
go to Settings -> Repositories -> Other Software Sources

Add these to your repository list.
 deb [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution main microverse non-free testing  
deb [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution main microverse non-free testing (only for 32-bit Ubuntu)
   deb [http://64.repository.backtrack-linux.org](http://64.repository.backtrack-linux.org) revolution main microverse non-free testing (only for 64-bit Ubuntu)
deb [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution main microverse non-free testing

Uncheck or remove (they are useless anyway) the newly added backtrack source repositories from the list.

Open up a terminal and run
```
you@computer:~$ wget -q [http://all.repository.backtrack-linux.org/backtrack.gpg](http://all.repository.backtrack-linux.org/backtrack.gpg) -O- | sudo apt-key add - 
you@computer:~$ sudo apt-get update && sudo apt-get upgrade
```You will already upgrade a couple of packages installed on Ubuntu to the ones in the Backtrack repositories.

2. Setting up the backtrack menu
IGNORE ANYTHING YOU HAVE GOOGLED ABOUT THIS BEFORE
```
you@computer:~$ sudo apt-get install backtrack-gnome-essentials backtrack-menu-icons
you@computer:~$ killall -9 gnome-panel
```backtrack-gnome-essentials installs the backtrack menu to your Gnome menu and backtrack-menu-icons installs the icons for the backtrack applications.
you need to kill the gnome panel to see the new icons instead of the "icon not found"-icons

I'm still looking for a way to see the backtrack menu specific icons, so if you find out how to see those, please post here. :)

I did this in Ubuntu 10.10 64-bit, but I guess it works for other Ubuntu versions using Gnome2 as well.

I was wondering if I can do it on Linux Mint Maya?

---

### Post by Zvlwab on 2012-06-13
I don't know, but I recently upgraded to Ubuntu 12.04 and now the 64-bit repo gives me errors.

---

### Post by nothingspecial on 2012-07-26
*Thread moved to **Outdated Tutorials & Tips**.*

---

