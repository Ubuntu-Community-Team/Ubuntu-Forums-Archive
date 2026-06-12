---
title: "error in latest updates"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-19
get the following when installing latest updates


```
The following packages will be upgraded:
  libgucharmap7
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,257 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 232873 files and directories currently installed.)
Preparing to replace libgucharmap7 1:3.0.1-0ubuntu1 (using .../libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgucharmap7 ...
dpkg: error processing /var/cache/apt/archives/libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgucharmap_2_90.so.7.0.0', which is also in package libgucharmap-2-90-7 1:3.1.92-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any help?

tempted to just wait & sit it out

---

### Post by mc4man on 2011-09-19
That seems to be the case - you could ck.for/file a bug on this.

---

### Post by mc4man on 2011-09-19
here
[https://bugs.launchpad.net/ubuntu/+source/gucharmap/+bug/853973](https://bugs.launchpad.net/ubuntu/+source/gucharmap/+bug/853973)

---

### Post by meborc on 2011-09-19
```
sudo apt-get -f install
``` maybe?!

---

### Post by flipper T on 2011-09-19
solved in latest updates.

all good things to those that wait / patience is a virtue etc etc

---

### Post by paul_in_london on 2011-09-19
> **flipper T said:**
> get the following when installing latest updates


```
The following packages will be upgraded:
  libgucharmap7
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,257 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 232873 files and directories currently installed.)
Preparing to replace libgucharmap7 1:3.0.1-0ubuntu1 (using .../libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgucharmap7 ...
dpkg: error processing /var/cache/apt/archives/libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgucharmap_2_90.so.7.0.0', which is also in package libgucharmap-2-90-7 1:3.1.92-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any help?

tempted to just wait & sit it out

Bit late on this occasion, but when this happens you can normally get round it with:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libgucharmap7_1%3a3.1.92-0ubuntu1_amd64.deb
```

---

