---
title: "how to uninstall"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by seyiisq on 2008-09-11
I need to uninstall a program which i recently install on my ubuntu os. pls how is this done

---

### Post by pastalavista on 2008-09-11
```
sudo aptitude remove <full name of app>
```

---

### Post by neurostu on 2008-09-11
It depends on how you installed it.
-If you installed with synaptic you can select the program for removal
-If you installed with apt-get install just use apt-get remove
-If you insatlled with make, make install, check to see if a remove script was included..

---

### Post by pastalavista on 2008-09-11
open a terminal and type
> **pastalavista said:**
> ```
sudo aptitude remove <full name of app>
```

---

### Post by seyiisq on 2008-09-11
sudo aptitude remove vmplayer
After using the above command i can still found that vmplayer is still up and running. pls can you help

---

### Post by seyiisq on 2008-09-11
pls can someone help

---

### Post by Tatty on 2008-09-11
How did you install vmplayer in the first place?  This is important as there are different methods of installing software in linux.

---

### Post by seyiisq on 2008-09-11
I downoaded vmware software, i changed into the directory of the folder downlaoded after which i ran

sudo ./vmware-install.pl

---

### Post by Michl on 2008-09-11
Did you reboot?

Also try this

```
sudo apt-get --purge remove vmplayer
```

---

### Post by zvacet on 2008-09-11
```
sudo dpkg --remove --force-remove-reinstreq vmplayer
```

---

### Post by halitech on 2008-09-11
> **seyiisq said:**
> I downoaded vmware software, i changed into the directory of the folder downlaoded after which i ran

sudo ./vmware-install.pl

try running```
sudo ./bin/vmware-uninstall.pl
``` from the terminal

---

### Post by jerome1232 on 2008-09-11
Just fyi you installed via pre-compiled binary, when install like that the software usually has it's own uninstaller program that came with it, if the author isn't so nice you have to manually remove the files it installed.

---

### Post by seyiisq on 2008-09-13
I have tried the above it isn't working do i have to go to the root directory to do the uninstallment

---

