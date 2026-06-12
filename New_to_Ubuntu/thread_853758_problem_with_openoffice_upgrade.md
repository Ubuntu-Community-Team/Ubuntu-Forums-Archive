---
title: "problem with openoffice upgrade"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by leeley on 2008-07-08
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-style-human_1%3a2.4.1-1ubuntu2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/share/config/images_human.zip')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-style-human_1%3a2.4.1-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
every time I try to do the upgrade I get the preceding

---

### Post by ChameleonDave on 2008-07-08
Do you get an error with other installations?  What happens if you run the following command?

```

sudo apt-get install -f

```

---

