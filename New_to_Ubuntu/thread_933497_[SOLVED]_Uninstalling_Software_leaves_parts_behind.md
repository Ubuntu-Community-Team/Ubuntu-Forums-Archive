---
title: "[SOLVED] Uninstalling Software leaves parts behind?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-09-29
In Windows whenever a person uninstalls any software, the uninstall program rarely works very well. Usually, after using a Windows uninstall program there are bits and pieces of the software scattered all over your computer; files are not all removed, and left over registry entries still remain. To get rid of this junk, I usually look for the software bits and pieces and registry entries manually, and then I manually delete them. 

I just uninstalled several programs from Ubuntu using the Synaptic Package Manager; I checked the options for the programs to uninstall with complete removal, including the configuration files.

Do Ubuntu (Linux) programs completely and cleanly uninstall from Ubuntu? 

Or, does this same problem --as desrcibed above for Windows-- also occur with Ubuntu (Linux) programs? 

JBA2337

---

### Post by oldsoundguy on 2008-09-29
My experience says yes, the stuff is removed as all of the dependency packages are also removed.  (which makes it really nice when you are trying to find that one program to do just what you want and no more and no less! Allows for experimentation!)
And there are not the miles of .reg files in Linux that abide in WinBLOAT.
But I could be off, I am not a programmer.  I am a user.

---

### Post by jerome1232 on 2008-09-29
Well they will leave behind configuration files, that way you can remove and reinstall those programs with out losing your settings.

To remove those configuration files as well you add the --purge option from the command line, or in synaptic mark them for complete removal.

```
sudo apt-get remove --purge programname
sudo apt-get autoremove --purge
```

---

### Post by oldsoundguy on 2008-09-29
I have opted for the complete removal every time I have removed a program.  Good to know I have been making the correct decision! LOL

---

