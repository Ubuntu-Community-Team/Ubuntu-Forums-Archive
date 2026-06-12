---
title: "all repositories"
date: 2005-03-12
forum: Repositories &amp; Backports
---

### Post by bigjoe on 2005-03-12
could someone write down _all_ repositories that can be used on hoary. marillat ones were not good...

peace,
bj.

---

### Post by bored2k on 2005-03-12
[QUOTE=bigjoe]could someone write down _all_ repositories that can be used on hoary. marillat ones were not good...

peace,
bj.[/QUOTE]
 ~$ cat /etc/apt/sources.list
deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

sure theyre not all though. You can get good ones with just selecting "show unselected/hidden" in synaptic.

---

