---
title: "Compile .deb file"
date: 2006-09-21
forum: Programming Talk
---

### Post by music_man on 2006-09-21
The programmer for the open source game "Annihilation" has almost finished the port to SDL and I would like to find out how to make a .deb file out of it.

So, how can I convert a tarball to .deb.

---

### Post by Sboulema on 2006-09-21
This is the basic way i create a deb file:

./configure
make
sudo checkinstall

checkinstall will ask a few questions and create the deb file. You can install checkinstall using apt-get or manually get it here: [http://asic-linux.com.mx/~izto/checkinstall/index.php](http://asic-linux.com.mx/~izto/checkinstall/index.php)

---

### Post by kperkins on 2006-09-21
> **Sboulema said:**
> This is the basic way i create a deb file:

./configure
make
sudo checkinstall

checkinstall will ask a few questions and create the deb file. You can install checkinstall using apt-get or manually get it here: [http://asic-linux.com.mx/~izto/checkinstall/index.php](http://asic-linux.com.mx/~izto/checkinstall/index.php)

That's the easy way, and good to make one for your own system, but is not the proper way.  And is definately not a good way for distributing a deb usable on many systems, since it doesn't do dependencies.
Check out these pages:
[http://wiki.inkscape.org/wiki/index.php/CompilingDebian](http://wiki.inkscape.org/wiki/index.php/CompilingDebian) (making a deb from inkscape tgz--nice tutorial)
[http://www.debian.org/doc/maint-guide/index.en.html#contents](http://www.debian.org/doc/maint-guide/index.en.html#contents) (Debain New Maintainers guide for building debs the proper way.)

---

