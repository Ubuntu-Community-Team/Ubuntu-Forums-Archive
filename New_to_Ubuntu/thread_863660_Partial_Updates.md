---
title: "Partial Updates"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-18
I am having trouble doing updates. It will only do partial updates and also there is something that dpkdg or somthing like that has to be run manually

---

### Post by avtolle on 2008-07-18
While your post leads me to guess, I'm guessing from the limited amount of information that you need to run from the CLI```
sudo dpkg --configure -a
``` to take care of the "something that dpkdg (*sic*) or something like that has to be run manually". This may clear up the partial update thing, too; or it may not, if there are updates being held back awaiting updated dependencies which are not yet ready, which will result in those being available for download once the dependencies are ready.

---

### Post by deadlySniper on 2008-07-18
ok now it says

A unresolvable problem occurred while intializing the package infomation.

Please report this bug against the 'update-manager' package and include the following error message:

'E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.'




I dont get this message or what to do.

---

### Post by deadlySniper on 2008-07-18
any help

---

### Post by deadlySniper on 2008-07-19
how do I unistall virtualbox

---

### Post by Kevbert on 2008-07-19
Best thing to do is run
```
sudo apt-get install -f
```
in terminal to repair any broken packages.  From there either the package will have been removed or fully installed.

---

### Post by Elfy on 2008-07-19
I had that once - this should do the trick as the install -f probably won't work.

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by deadlySniper on 2008-07-19
Run a partial upgrade, to install as many updates as possible

This can be caused by:
*A previous upgrade which didnt complete
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-releease version of Ubuntu



Should I just do the update and the upgrade

---

