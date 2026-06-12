---
title: "modern version of texlive in Ubuntu 11.10?"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pythonscript on 2011-09-16
Is there any chance of an actually *recent* version of texlive being included in Ubuntu 11.10? I searched on packages.ubuntu.com, and it still shows the 2009 version. New features are added all the time, and for those of us that install texlive-full, is our only option for getting something anywhere close to recent installing from the site? Having recently had problems installing that version, it seems a shame that the repository hasn't been updated in at least 3 versions of Ubuntu. 

Have the Ubuntu developers considered updating this crucial piece of the repositories?

---

### Post by ronacc on 2011-09-16
there are several ways to get the latest version here  
[http://www.tug.org/texlive/acquire.html](http://www.tug.org/texlive/acquire.html)
if the ubuntu maintainers aren't updating your favorite prg , do an end run around them and update it yourself .

---

### Post by pythonscript on 2011-09-16
Right, I know about the version on their site, as I said in the OP, I was just wondering if the developers were planning to ever update the version in the repository, since it makes the system a lot more stable (and easier to use) the more packages that are directly installable from the repos. Hopefully by the time the next LTS version comes out, the repos version will have been updated.

---

### Post by ronacc on 2011-09-16
the sad truth is that in a fragmented ecosystem such as the linux community there are not enough devs even in major distros like Ubuntu to keep everything up to date and integrated all the time , either through lack of resources or lack of intrest .  It is sometimes necessary to take matters into your own hands and really it is not all that difficult most of the time . I regularly install packages directly from the providers or from the debian repos and rarely have stability problems even when I compile from source .

you can file to the wishlist or bug the package as out of date .

---

### Post by jbicha on 2011-09-17
It looks like texlive releases a new stable version about once a year but Debian is on more of a 2-year cycle. And the 2009 version is still being maintained by Debian; the -13 update just landed a month ago.

Upstream says that not much changed in 2011, but 2010 had some changes: [http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#news](http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#news) . Texlive is a massive project which takes a large amount of time to package and keep things working reliably and predictably even through upgrades.

---

