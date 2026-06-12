---
title: "malformed line 16 in source list"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Geist in the shell on 2012-10-07
Hi!, it's another software package manger error thread!
just installed 12.04 over Mint Katya, and i already have an error

```
E: Malformed line 16 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

``````
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
deb http://packages.linuxmint.com/ precise main upstream import
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner
deb http://extras.ubuntu.com/ubuntu precise main
deb http://packages.medibuntu.org/ precise free non-free

# deb http://archive.getdeb.net/ubuntu natty-getdeb apps
# deb http://archive.getdeb.net/ubuntu natty-getdeb games

# Remastersys[B]
deb http://www.geekconnection.org/remastersys/repository precise[/B]


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
```Does this error mean that this source link is dead?
what do i do here?

*also, what is natty doing in line 13-14? the installation disc was 12.04*

---

### Post by Bucky Ball on 2012-10-07
Go to Software Sources (or open update manager>'Settings' at bottom left) and disable the 'deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) precise' as a source. ;)

---

### Post by Sef on 2012-10-07
> # Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) precise


Put a # in front of the bottom line. Hence it should look like this:

```
# Remastersys
# deb http://www.geekconnection.org/remastersys/repository precise
```

The # means (in a basic sense) do not read this line.

---

### Post by Bucky Ball on 2012-10-07
> **Sef said:**
> Put a # in front of the bottom line. Hence it should look like this:

```
# Remastersys
# deb http://www.geekconnection.org/remastersys/repository precise
```

+1. Yep, or that. ;)

---

### Post by Geist in the shell on 2012-10-07
thanks for such fast replies! sudo updated, and software manager started w/o problems
but i got these (errors?) notices in log when the update finished
```
Fetched 17.4 MB in 1min 13s (237 kB/s)                                         
W: Failed to fetch http://packages.linuxmint.com/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.linuxmint.com/dists/precise/upstream/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.linuxmint.com/dists/precise/import/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.linuxmint.com/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.linuxmint.com/dists/precise/upstream/binary-i386/Packages  404  Not Found

W: Failed to fetch http://packages.linuxmint.com/dists/precise/import/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

is this something that needs fixing?

---

### Post by Bucky Ball on 2012-10-07
Yea, you still have the Linuxmint repos enabled. Disable.

---

### Post by Geist in the shell on 2012-10-07
I give up, how do I go about disabling them?

---

### Post by Bucky Ball on 2012-10-07
> **Bucky Ball said:**
> Go to Software Sources (or open update manager>'Settings' at bottom left) and disable the 'deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) precise' as a source. ;)

Like that, except look for the offending repo(s) rather than the one in the example and untick.

---

