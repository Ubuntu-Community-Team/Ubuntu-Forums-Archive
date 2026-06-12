---
title: "Compile error for Gnucash"
date: 2007-05-16
forum: Programming Talk
---

### Post by bpont on 2007-05-16
I followed the instructions at: [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian) to build and install Gnucash with HBCI and aqofxconnect enabled and compilation exited with the following errors:

```
chmod u+x ./iso-currencies-to-c
GUILE_LOAD_PATH=: srcdir=. ./iso-currencies-to-c
ERROR: Could not find slib/require.scm in  ("" "" "/usr/share/guile/site" "/usr/share/guile/1.8" "/usr/share/guile")
make[4]: *** [iso-4217-currencies.c] Error 1
make[4]: Leaving directory `/home/dhamma/gnucash/gnucash-2.0.2/src/engine'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dhamma/gnucash/gnucash-2.0.2/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dhamma/gnucash/gnucash-2.0.2'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dhamma/gnucash/gnucash-2.0.2'
make: *** [build-stamp] Error 2
```

Any help is appreciated.  Thanks.

---

### Post by public_void on 2007-05-16
Install it from the repositories.

```
sudo apt-get install gnucash
```

As for compiling, I guessing you may need the guile slib support package. Its seems to be looking in /user/share/guile for a slib directory.

```
sudo apt-get install guile-1.6-slib
```

Note: I'm running Dapper and so the latest guile slib package may not be 1.6.

---

### Post by bpont on 2007-05-16
> **public_void said:**
> Install it from the repositories.

```
sudo apt-get install gnucash
```

As for compiling, I guessing you may need the guile slib support package. Its seems to be looking in /user/share/guile for a slib directory.

```
sudo apt-get install guile-1.6-slib
```

Note: I'm running Dapper and so the latest guile slib package may not be 1.6.

Apparently, I already have it installed:

```
Reading state information... Done
guile-1.6-slib is already the newest version.
```

Also, I have this in my tree:

```
/usr/share/guile/1.8/ice-9/slib.scm
/usr/share/guile/1.6/slib
/usr/share/guile/1.6/slibcat
/usr/share/guile/1.6/ice-9/slib-old.scm
/usr/share/guile/1.6/ice-9/slib.scm
```

---

### Post by public_void on 2007-05-17
Should have adding that before, how about guile-1.6-dev? Normally when compiling you need the dev packages.

---

### Post by bpont on 2007-05-17
> **public_void said:**
> Should have adding that before, how about guile-1.6-dev? Normally when compiling you need the dev packages.

I have that too, apparently...

```
Reading state information... Done
guile-1.6-dev is already the newest version.
```

What else could it be?

---

### Post by jawahar on 2007-08-10
I believe I have found the error. Use Synaptic to remove the package guile-1.8

Note that this will also remove "songwrite" and "lilypond" if they are installed. After that ./configure or the other methods to install gnucash work perfectly.

---

### Post by theophile on 2008-05-24
I second that. Removing guile-1.8 fixed compile problems with SLIB and GnuCash 2.2.5.

---

