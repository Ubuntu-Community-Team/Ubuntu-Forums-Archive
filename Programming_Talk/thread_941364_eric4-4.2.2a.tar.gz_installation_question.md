---
title: "eric4-4.2.2a.tar.gz installation question"
date: 2008-10-08
forum: Programming Talk
---

### Post by hoboy on 2008-10-08
I have sudo apt-get install eric to install it, when I launched it
it ask for the update that led me to the download eric4-4.2.2a.tar.gz, I have download it, how can I install it ?

---

### Post by Partyboi2 on 2008-10-09
If you have installed eric from the ubuntu repo's you should be able to upgrade by
```
sudo apt-get upgrade
``` The version in the ubuntu repos is 4.1.1. You can check what version you have by 
```
dpkg -l eric
``` If you are wanting to use a more current version that is not in the ubuntu repos then you can compile it from source. If this is what you are wanting to do then extract the eric4-4.2.2a.tar.gz by either right clicking on it and choosing to extract, or from the directory of the downloaded file
```
tar xvzf eric4-4.2.2a.tar.gz
``` then read the readme and the install file.
[B]
[/B]

---

