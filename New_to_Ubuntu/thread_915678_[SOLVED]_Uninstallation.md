---
title: "[SOLVED] Uninstallation"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by balahh on 2008-09-10
How do you uninstall programs in Ubuntu? I don't know how to uninstall LimeWire (Linux version), iTunes, and QuickTime and I really need help. Thanks to the future replies :)

---

### Post by Bliepo32 on 2008-09-10
```
sudo apt-get autoremove [packagename]
```

---

### Post by balahh on 2008-09-10
That command doesn't seem to work. It says that it couldn't find the package. :confused:

---

### Post by kpkeerthi on 2008-09-10
Open System -> Admin -> Synaptic. Search for the package and mark for Complete Removal and click Apply.

* Note: This will only work if you installed the packages using .deb files or apt-get/aptitude from the repositories.

There is no iTunes for linux. How did you install it? That might answer how you may remove it.

---

### Post by Dill on 2008-09-10
The package might be named something you might not expect... for limewire, try this...

```
dpkg --list | grep -i lime
```

And you should see a list of all the packages containing the characters "lime"; once you know the name of the limewire package, try this:

```
sudo apt-get --purge remove 'name_of_package' 
```

Also, did you install iTunes and Quicktime through Wine?

Cheers, 
Dylan

---

### Post by balahh on 2008-09-10
Thank you that worked for LimeWire :) As for iTunes and QuickTime, yes I used Wine but everytime I try to uninstall QuickTime the screen goes black and a window pops up that says I have successfully installed QuickTime. For iTunes, I have no idea how to uninstall it also.

---

### Post by kpkeerthi on 2008-09-10
> 
Open up a terminal window and type "uninstaller" - this will open up a program similar to Windows' "add/remove programs" control panel, allowing you to uninstall applications from a Wine installation. Running uninstall programs directly via Wine should also work normally. Alternatively, you could also simply delete the folder of the application. However, as when done in Windows, this method will be "unclean" and will not remove the program's configuration from the Wine registry like using an uninstaller will.
... from [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Look in ~/.wine for a folder where wine apps are installed.

---

