---
title: "what command to use exactly for complete removal of an application from ubuntu 10.04?"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2013-05-01
okay there are many options i got in internet to remove any application completely from the ubuntu system (along with configuration files from the whole system so that if i install the same application again it's a fresh install then) like-

sudo apt-gt purge...
sudo apt-get --purge remove...
sudo apt-get autoremove...
sudo apt-get --purge autoremove...
sudo apt-get install purge...



it's confusing! which one to use definitely??

---

### Post by oldos2er on 2013-05-01
```
sudo apt-get purge <package>
``` You'll need to delete any configuration files in your home folder manually.

---

### Post by Frogs Hair on 2013-05-01
I use the following and if the application name is more than one word use a dash. Alternatively you can install the synaptic package manager and mark the package for complete removal and then remove residual configuration. Synaptic is a nice tool, but no longer a default package.     

```
sudo apt-get remove --purge package-name
```

---

### Post by papibe on 2013-05-01
Hi tojonukokhadush.

**remove** uninstall a package from your system.

**purge** is **remove** + delete config files and delete downloaded .deb

**autoremove** looks for packages that were installed to support other packages which are no longer installed.

**--purge remove** is the same as purge.

**--purge autoremove** adds the deletion of config files and .debs to the autoremove function.

**--purge install** AFAIK is a valid, but bizarre, way of installing a package. Not sure if it works, or the desire outcome.

There's more information on the man:
```
man apt-get
```

Does that help?
Regards.

---

### Post by 3rdalbum on 2013-05-01
If you want it to be like it was only just installed, you need to remove its settings files from the hidden directories in your home folder.

---

### Post by tojonukokhadush on 2013-05-02
yeah! thank you all, those were really useful! special thanks to papibe!

---

### Post by tojonukokhadush on 2013-05-02
and Mr. Frogs Hair, i wish to be more clear on [COLOR=#000000]"remove residual configuration"! thanks in advance.[/COLOR]

---

