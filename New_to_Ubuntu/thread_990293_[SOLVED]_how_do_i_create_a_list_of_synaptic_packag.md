---
title: "[SOLVED] how do i create a list of synaptic packages i.ve already downloaded?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-11-22
Hi

I really just want a list of already installed packages in a text document which i can copy into a terminal, and it downloads them all - since i am upgrading to 8.10

cheers!

---

### Post by bobnutfield on 2008-11-22
> dpkg --get-selections > installed-software

This will create a text file of all of the installed software.  It will include EVERYTHING, including software from your original install.

---

### Post by Tomatz on 2008-11-22
Synaptic (apt) wont uninstall your packages when you upgrade. It will simply upgrade them to newer versions.

You wont have to reinstall anything, except (possibly) complied apps.


;)

---

### Post by phantomjoker on 2008-11-22
sorry - when i sed upgrading - i am also upgrading my pc too - so my hdd is going.... so its all on a fresh system.



... i tried 
```
dpkg --get-selections > installed-software
```
and it did nothing. I then tried
```
dpkg --get-selections > installed-software *.*
```
and it said 
> No packages found in untitle.txt
No packages found in winged.jpg
.... and carried on through all my files in my documents...

---

### Post by shifty_powers on 2008-11-22
the first one did work.

check your home directory for a text file installed-software

---

### Post by bobnutfield on 2008-11-22
It will not return anything on the command line, but there should be a file in your home directory called "Installed Software."

---

### Post by phantomjoker on 2008-11-22
oh, my bad... how embarresingly simple was that...

cheers!

---

### Post by bobnutfield on 2008-11-22
You can edit that file and remove any software you do not want to reinstall (such as some system files.)  When you are ready to reinstall, you simply take that file in your home directory and issue:

> dpkg --set-selections < installed-software

dselect

But be aware that some software may not play nice with a new version of Ubuntu.

---

### Post by drs305 on 2008-11-22
> **bobnutfield said:**
> But be aware that some software may not play nice with a new version of Ubuntu.

The good thing about it is that it will be drawing the packages from the repositories and if only the 'official' repositories are enabled everything that is installed should be ok. Note this is about software; hardware may be another issue.

---

### Post by Wickd on 2008-11-22
You can also navigate to the following directory using either the terminal or nautilus:

/var/cache/apt/archives

Here you will find all the packages that have been installed via aptitude (synaptic package manager)

You can copy them to your new archives directory of your new installation and save yourself some cap. Worked fine for me

Cheers

---

### Post by Tomatz on 2008-11-23
As i have explained, its completely pointless. All packages installed via synaptic will be upgraded _not_ removed.


;)

---

