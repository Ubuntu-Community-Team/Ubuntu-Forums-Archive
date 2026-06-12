---
title: "flash player?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-09
I have the x86_64 architecture and it says that my architecture isnt supported when I try and install adobe flash player v9.

I found manual install directions online, but I am missing files in the .tar.gz that it mentions (they are not hidden as in ".file") I only have the script to install and the .so file.

---

### Post by oldos2er on 2008-10-09
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Therion on 2008-10-09
Go to Applications/Add/Remove...
Set Show: to All available applications
Search for **ubuntu-restricted-extras** and install it.

Or```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by philinux on 2008-10-09
> **Therion said:**
> Go to Applications/Add/Remove...
Set Show: to All available applications
Search for **ubuntu-restricted-extras** and install it.

Or```
sudo apt-get install ubuntu-restricted-extras
```
+1 for that.

The flash is still 32bit but the restricted extras package installs it correctly using nspluginwrapper.

---

### Post by Nepherte on 2008-10-09
Or if you'd like to install the flash player only:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Sycron on 2008-10-10
Well, it works ?

---

