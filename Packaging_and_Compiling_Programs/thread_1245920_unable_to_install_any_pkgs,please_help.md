---
title: "unable to install any pkgs,please help"
date: 2009-08-21
forum: Packaging and Compiling Programs
---

### Post by wrapster on 2009-08-21
Hi all,
Im having issues installing any pkg...

Here is the result.
#apt-get install mercurial-common
...
..
you might want to run apt-get -f install' to correct these
following pkg have unmet dependencies
sunwspro: depends on sprosslnk but its not going to be installed

so I  did this,
#apt-get install sprosslnk
....
....
dpkg: Error processing /var/cache/apt/archives/sprosslnk_12_200709_......deb
trying to overwrite /usr/bin/c++filt which is also in pkg bintuils.
E: sub-process /usr/bin/dpkg returned with error code(1)
...............

Can anyone please help me.. Im unable to install any pkgs coz of this.

Thanks

---

### Post by arky on 2009-08-23
You can get rid of the package or use force to overwrite the file.

---

