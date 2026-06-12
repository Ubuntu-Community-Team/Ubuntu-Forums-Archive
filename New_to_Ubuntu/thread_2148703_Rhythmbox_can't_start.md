---
title: "Rhythmbox can't start"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by Jpox on 2013-05-26
Hi,

I'm a user of Kubuntu 12.04 LTS and I have a problem with Rhythmbox.

When I type in a terminal:

 rhythmbox

I get the message:

rhythmbox: error while loading shared libraries:  libtotem-plparser.so.17: cannot open shared object file: No such file or  directory

and when I type:

 sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.17

as someone suggested I get:

 cp: cannot stat `/usr/lib/libtotem-plparser.so': No such file or directory

I tried to reinstall Rhythmbox but I get the same error.

Could someone help me?

Thank you very much.

---

### Post by mc4man on 2013-05-26
The cp idea was wrong & ill-advised  (there is no libtotem-plparser.so file & libtotem-plparser.so.17 is  a symlink to libtotem-plparser.so.17.0.3

libtotem-plparser17 is a dep of rhythmbox so should be installed, ck. here on whether it is & version
```
apt-cache policy libtotem-plparser17
```

Also what does this show - 
```
ls -la /usr/lib |grep libtotem-pl
```

Ex. here - 
> $ ls -la /usr/lib |grep libtotem-pl
lrwxrwxrwx   1 root root           32 Mar 24 18:43 libtotem-plparser-mini.so.17 -> libtotem-plparser-mini.so.17.0.3
-rw-r--r--   1 root root        17928 Apr 17  2012 libtotem-plparser-mini.so.17.0.3
lrwxrwxrwx   1 root root           27 Mar 24 18:43 libtotem-plparser.so.17 -> libtotem-plparser.so.17.0.3
-rw-r--r--   1 root root       117140 Apr 17  2012 libtotem-plparser.so.17.0.3

---

### Post by Jpox on 2013-05-26
Thank you very much for your reply.

I type:

apt-cache policy libtotem-plparser17

and I get:

libtotem-plparser17:
  Installed: 3.4.1-1
  Candidate: 3.4.1-1
  Version table:
 *** 3.4.1-1 0
        500 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status
 

then I type:

ls -la /usr/lib |grep libtotem-pl

and I get:

-rw-r--r--   1 root root       238996 Apr 17  2012 libtotem-plparser.a
-rw-r--r--   1 root root        40286 Apr 17  2012 libtotem-plparser-mini.a
lrwxrwxrwx   1 root root           32 Apr 17  2012 libtotem-plparser-mini.so -> libtotem-plparser-mini.so.17.0.3
lrwxrwxrwx   1 root root           27 Apr 17  2012 libtotem-plparser.so -> libtotem-plparser.so.17.0.3

It seems a bit different from yours. Now what have I to do?

---

### Post by mc4man on 2013-05-26
The .a files & the symlinks  libtotem-plparser.so  &  libtotem-plparser-mini.so  are from the libtotem-plparser-dev package

You seem to be missing the links from the libtotem-plparser17 package, that's why Rb is faiing to open

You could either purge  libtotem-plparser17 & re-install it & all the other packages removed or just create the links - 

```
sudo ln -s  /usr/lib/libtotem-plparser.so.17.0.3  /usr/lib/libtotem-plparser.so.17
```
```

sudo ln -s  /usr/lib/libtotem-plparser-mini.so.17.0.3  /usr/lib/libtotem-plparser-mini.so.17
```

---

### Post by Jpox on 2013-05-27
Thank you very much mc4man!!

I remove and reinstall libtotem-plparser17 and all others packages RB needs, and now RB works!!

Thank you for your help!!

---

