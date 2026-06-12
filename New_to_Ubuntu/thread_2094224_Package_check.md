---
title: "Package check"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by rezaf on 2012-12-13
Hi,
how can I know that this packages are installed on my ubuntu 9.10 or not ?
also how can I install them if aren't installed ?

binutils, gcc, glibc development files, ncurses, zlib, texinfo, GTK+, QT, TCL/TK, host side kernel source

thanks.

---

### Post by sahabcse on 2012-12-13
Try the below command

dpkg --get-selections | grep binutils

If it is not display any output , Then run

apt-get install binutils

Do the same for other packages too.

---

### Post by Zill on 2012-12-13
rezaf:  Ubuntu 9.10 reached [end-of-life]("https://wiki.ubuntu.com/Releases") on April 30, 2011 and is therefore no longer supported.  I recommend you upgrade to a supported release, such as Ubuntu 12.04 LTS (supported until April 2017) or Ubuntu 12.10 (supported until April 2014).

The "Software Center" in your release will show you which packages are installed and allow the easy installation of any other required packages.

The packages you have listed imply that you intend to do some development work on your system.  With all due respect, I suggest you may like to first use your upgraded system "as is" in order to learn basic Linux functionality before you start any development work as this could, potentially, break your system!

---

### Post by MButterman on 2012-12-14
I would research the upgrade from 9.10 to 12.04. I would think the better route would be to backup what you wish to save then do a clean install of 12.04. The package that has most of the utilities for compiling would be the "build-essential" there might be other packages but that would cover most of your needs. Also there is a "README" file that outlines what is required to compile that package. 

On a clean install of 12.04 LTS, type

```
sudo apt-get install build-essential
```

---

