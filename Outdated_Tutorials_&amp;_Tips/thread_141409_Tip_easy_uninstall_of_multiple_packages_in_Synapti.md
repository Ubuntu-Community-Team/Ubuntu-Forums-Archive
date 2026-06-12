---
title: "Tip: easy uninstall of multiple packages in Synaptic"
date: 2006-03-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Jucato on 2006-03-08
Just wanted to share a trick I discovered in Synaptic. I don't know if this is documented or old news. But might be helpful for new people. This tip is for uninstalling multiple packages using Synaptic

1. When you are about to install multiple packages, for example more than 5 packages, before hitting the Apply button, go to the File menu and choose Save Markings/Save Markings As. This will save the marked changes (install or remove) into a text file. The text file will look something like this:

```
lockfile-progs		install
htdig		install
libdb2		install
liblockfile1		install
```

If during the installation, some packages had to be removed (because of dependencies), they will be marked with "deinstall"

2. If you weren't able to save the markings before applying the changes, you can check the File > History for what you did. Copy the appropriate list (on the date and time you did the installation) into a text file. It would look something like this at first: 

```
Commit Log for Fri Feb 17 13:26:20 2006


Installed the following packages:
gcc-3.3-base (1:3.3.6-8ubuntu1)
libstdc++5 (1:3.3.6-8ubuntu1)
```

Remove the Commit Log line, the "Installed the following packages" and the version numbers including the parentheses, leaving you with just the package names. It would look something like this:

```
gcc-3.3-base
libstdc++5
```

3. When you want to uninstall the packages, open the file that you saved in step 1 or 2, and using your favorite text editor, change all "install" words into "deinstall" and those marked with "deinstall" into "install" (to reinstall the removed packages that might be needed by the system)

4. In synaptic, go to the File menu and choose Read Markings. Load your text file, and it will automatically mark the changes. Double-check and hit Apply.

Of course this works only if you installed the packages through Synaptic.

An easier alternative in installing multiple packages is through apt-get install, saving the package names into a text file, and pasting the names again when you want to apt-get remove.

As far as I know, Synaptic is the only package manager that has these features. Kynaptic, KPackage, and Adept don't.

Hope this little bit helps to make life a bit easier :D

---

### Post by Klaidas on 2006-03-08
Nice feature, I didn;t know about that since now :)

---

