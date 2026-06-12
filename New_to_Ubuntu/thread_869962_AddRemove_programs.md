---
title: "Add/Remove programs"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Norfolk 'n' Good on 2008-07-25
Hi

In windows, if I wanted to remove a program, I would have used add/remove programs in control panel.  Is there a simple terminal command that does the same thing?  I installed vmware and now wish to remove it, however there are bits of it everywhere.

Cheers.

---

### Post by Seisen on 2008-07-25
> **Norfolk 'n' Good said:**
> Hi

In windows, if I wanted to remove a program, I would have used add/remove programs in control panel.  Is there a simple terminal command that does the same thing?  I installed vmware and now wish to remove it, however there are bits of it everywhere.

Cheers.

How did you install vmware?

---

### Post by gimlithedwarf on 2008-07-25
if you installed vmware from a debian package type ```
sudo apt-get remove vmwarepackagename
``` if you compiled it yourself using vmwares perl script i beleive they leave an uninstaller script somewhere after the install. My guess is that it will be somewhere like /usr/local/vmware or /usr/share/vmware

---

### Post by cprofitt on 2008-07-25
if you installed vmware with a .deb file yes... if not... then I do not believe there is any 'easy' way to do that.

If you installed an app with a .deb you should be able to use apt-get remove <appname>

---

### Post by boblemur on 2008-07-25
im not sure but you should be able to use 

```
sudo apt-get remove vmware
```

or search for it in synaptic package manager if you dont know the exact name of the package...

---

### Post by H3retic on 2008-07-25
You can either use the add/remove dialog under programs, or use the synaptic package manager (placed in Settings somwhere) and remove the specific packages.

There is a terminal command, but I'm afraid I'm not that savvy ;)

---

### Post by BDNiner on 2008-07-25
How did you install it? if you downloaded the latest version from vmware site then there should be an uninstall script in the archive that you downloaded. you could also try
```

sudo dpkg --purge *vmware*

```

i don't know the name of the vmware package so replace *vmware* with the actual name of the package.

---

### Post by Norfolk 'n' Good on 2008-07-25
I downloaded vmware onto my desktop, extracted it from the .tar and in the terminal I located he folder and typed 'sudo ./vmware-install.pl'.  From there I followed the prompts.

---

### Post by Seisen on 2008-07-25
Try this,

```
sudo ./vmware-uninstall.pl
```

---

### Post by david sousa on 2008-07-25
Simply go to synaptic packages manager at system-> administration and everything you have is there. Do search "Vmware" and right click in the green mark that corresponds to the program. Then aply!

:D

---

### Post by TBOL3 on 2008-07-25
There is also an application that removes orphaned dependencies.  Go to add/remove, and install Remove orphaned packages.

---

### Post by Methuselah on 2008-07-25
> **Seisen said:**
> Try this,

```
sudo ./vmware-uninstall.pl
```

Listen to this man.
This is the proper way to uninstall it.
VMWare has its own install and uninstall perl scripts.

---

