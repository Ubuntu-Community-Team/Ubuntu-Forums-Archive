---
title: "Build a binary Deb from a Github clone"
date: 2014-02-03
forum: Packaging and Compiling Programs
---

### Post by narcisgarcia on 2014-02-03
I've tried checkinstall with no success ( [http://sourceforge.net/apps/trac/lemonpos/ticket/210](http://sourceforge.net/apps/trac/lemonpos/ticket/210) ).
Project's documentation is obsolete, and doesn't cover packaging actions ( [http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide](http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide) )
The updated procedure to simply install latest version of the software (without package managing) is:
```

sudo apt-get --install-recommends install build-essential git cmake
sudo apt-get --no-install-recommends install kdelibs5-dev
git clone https://github.com/miguelchavez/lemonpos.git
cd lemonpos/
git fetch origin persa:persa
git checkout persa
git pull origin persa
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
make
sudo make install
```

I've found a lot of large and complicated manuals about compiling and packaging, but I suppose that there is some easier way to generate a deb from this.
Am I right?

---

### Post by Bachstelze on 2014-02-03
> **narcisgarcia said:**
> 
I've found a lot of large and complicated manuals about compiling and packaging, but I suppose that there is some easier way to generate a deb from this.
Am I right?

Basically, no. checkinstall is the quick and dirty way, but if it doesn't work I think your only option is to follow the [packaging guide]("http://packaging.ubuntu.com/html/").

---

