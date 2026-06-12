---
title: "If you manually install a .deb file..."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-17
... and want to remove it later on, what do you do if you don't remember the name of the package?

Example: I download a .deb file, double-click on it to install it. It installs, as it should... now lets say I delete that .deb file and later on want to remove the program. It can't be removed because it doesn't show up in synaptic (the repo hasn't been updated with the latest version yet)... and I don't remember the exact name of the package. What then? 

I've asked this question before, but I'm still confused. 

-'Mage

---

### Post by vexorian on 2008-05-17
It really should show in synaptic once you install it. Look under the installed or the local filters.

---

### Post by empthollow on 2008-05-17
you can still uninstall it.  It should actually show in synaptic because dpkg keeps a list of all installed packages.  If you can't find it in synaptic you could try
```
dpkg -l | grep program_name
```
this will output a list of similarly named install packages, if you see your package name there type:
```
sudo dpkg -r package_name_X.XX
```
to remove unused dependencies type:
```
sudo apt-get autoremove
```

---

### Post by HotShotDJ on 2008-05-17
> **UnWarierMage224 said:**
> It can't be removed because it doesn't show up in synaptic (the repo hasn't been updated with the latest version yet)... and I don't remember the exact name of the package. What then? Any deb package that you installed... either through Synaptic, apt-get install, dpkg -i, gdebi... whatever... WILL show up in Synaptic.  What do you remember about the package?  You might try to use the search function in Synaptic Package Manager to try to find it using some key word. Failing that, you might use Google to figure out the exact name of the package. But without having some clue as to what the software you installed was, one would be hard-pressed to figure out how to remove it.

---

### Post by vexorian on 2008-05-17
Synaptic's "Installed (Local or obsolette)" filter shows all the installed packages that don't have a repository image.

---

### Post by antwerx on 2008-05-17
I am not sure either, hopefully some folks will chime in, but I think there is a dpkg command to list all packages installed on a system.  You can man dpkg and maybe find the command.  Then once you know the package that was installed you can remove the package using dpkg once again.

Hope this will get some responses that actually lists the commands.

Hang in there, keep searching this forum, searching google and excercising the man pages...you just might get your answer sooner rather than later.

---

### Post by empthollow on 2008-05-17
```
dpkg -l
```
is the command that lists all packages installed on the system.

---

### Post by UnWarierMage224 on 2008-05-17
Indeed, it does show up in synaptic. 

Thanks, all. 

-'Mage.

EDIT: One more somewhat-related question... If I compile a package from source and install it, will it still be removable through Synaptic using this local/obsolete filter? Or will more intensive methods be required to remove it?

---

### Post by empthollow on 2008-05-17
you will have to use another method to uninstall *UNLESS* :) instead of doing make install you use the checkinstall command.  It will create a .dep package and install it so that you can uninstall it easily and transport it btw systems.

---

### Post by HotShotDJ on 2008-05-17
> **UnWarierMage224 said:**
>  If I compile a package from source and install it, will it still be removable through Synaptic using this local/obsolete filter? Or will more intensive methods be required to remove it?Please, for your own sanity, use CheckInstall when compiling packages from source.  See [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by vexorian on 2008-05-17
> **empthollow said:**
> you will have to use another method to uninstall *UNLESS* :) instead of doing make install you use the checkinstall command.  It will create a .dep package and install it so that you can uninstall it easily and transport it btw systems.
Yes, like the others said (would like this to be clear), the manuals will tell you to

```

make install

```

Instead , you have to use
```

sudo checkinstall

```
And you would be able to uninstall it, it will also prevent you from doing "bad" things.

---

### Post by UnWarierMage224 on 2008-05-18
OK, cool. 

Thanks for the pointers, everyone. 

-'Mage

---

