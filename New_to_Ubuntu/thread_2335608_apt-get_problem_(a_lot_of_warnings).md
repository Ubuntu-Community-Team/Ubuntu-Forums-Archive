---
title: "apt-get problem (a lot of warnings)"
date: 2016-08-30
forum: New to Ubuntu
---

### Post by urosvgd on 2016-08-30
I gave my computer to buddy, when he returned it to me and i tried to update my system with apt-get update and
here is what happens...

```

sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/multiverse Sources [179 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main Sources [868 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/universe Sources [7728 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/restricted Sources [4808 B]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports/main Sources [1400 B]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe Sources [800 B]
Get:9 http://security.ubuntu.com/ubuntu xenial-security InRelease [94,5 kB]                       
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [8952 B]                
Fetched 94,5 kB in 8s (11,4 kB/s)                                                                 
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (deb/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (deb/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11 (deb/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11-icons (deb/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11 (http://us.archive.ubuntu.com/ubuntu//dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11-icons (http://us.archive.ubuntu.com/ubuntu//dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (xenial-updates/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (xenial-updates/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (xenial-updates/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (xenial-updates/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (xenial-updates/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11 (xenial-updates/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11-icons (xenial-updates/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (deb/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (deb/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (deb/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (deb/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11 (deb/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11-icons (deb/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11 (http://us.archive.ubuntu.com/ubuntu//dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11-icons (http://us.archive.ubuntu.com/ubuntu//dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (xenial-updates/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (xenial-updates/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (xenial-updates/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (xenial-updates/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (xenial-updates/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11 (xenial-updates/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11-icons (xenial-updates/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Unable to find expected entry 'deb/source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Unable to find expected entry 'deb/source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Unable to find expected entry 'deb/source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:3
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (deb/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (deb/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11 (deb/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11-icons (deb/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11 (http://us.archive.ubuntu.com/ubuntu//dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11-icons (http://us.archive.ubuntu.com/ubuntu//dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (xenial-updates/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (xenial-updates/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (xenial-updates/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (xenial-updates/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (xenial-updates/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11 (xenial-updates/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target DEP-11-icons (xenial-updates/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:5
W: Target Packages (deb/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (deb/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (deb/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (deb/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (deb/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11 (deb/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11-icons (deb/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (http://us.archive.ubuntu.com/ubuntu//binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (http://us.archive.ubuntu.com/ubuntu//i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11 (http://us.archive.ubuntu.com/ubuntu//dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11-icons (http://us.archive.ubuntu.com/ubuntu//dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (xenial-updates/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (xenial-updates/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Packages (xenial-updates/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (xenial-updates/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target Translations (xenial-updates/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11 (xenial-updates/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7
W: Target DEP-11-icons (xenial-updates/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:7

```


If anyone can help, I'd be grateful!

---

### Post by Bashing-om on 2016-08-30
urosvgd; Hello;

The system is telling you exactly what the problem is . duplicated sources.
And relies on you to fix it.
So we look and see where the damage is, and what needs to be done to rectify:
Post back - between code tags - the out puts of terminal commands :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And we fire up a text editor to resolve this situation .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-08-30
...and don't lend your system to that buddy anymore.

---

### Post by urosvgd on 2016-08-30
Okay, i did this
```

cat -n /etc/apt/sources.list
     1	deb http://us.archive.ubuntu.com/ubuntu/ xenial main universe
     2	deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse main universe restricted deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates #Added by software-properties
     3	deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
     4	
     5	deb http://us.archive.ubuntu.com/ubuntu/ xenial universe deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
     6	
     7	deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
     8	
     9	deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    10	deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse deb http://security.ubuntu.com/ubuntu xenial-security main restricted #Added by software-properties
    11	
    12	deb http://security.ubuntu.com/ubuntu xenial-security universe deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    13	deb-src http://security.ubuntu.com/ubuntu xenial-security universe deb http://security.ubuntu.com/ubuntu xenial-security multiverse #Added by software-properties

```
and this
```

tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open '/etc/apt/sources.list.d/*' for reading: No such file or directory

```
P.S. I'm new in linux world.

---

### Post by Bashing-om on 2016-08-30
urosvgd; Ouch !

What has been done !
I think the easiest way out here is to replace your config file with mine:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
#deb-src http://archive.canonical.com/ubuntu xenial partner

```
or you may prefer to edit your existing file to be the same as this .
As you can see in my file there is the proper formatting, and only one fetch per line. Someone has sure messed up your file with double entries on lines .. and some sources are duplicated .
Just depends on which way tou want to handle this, what you are the more comfortable doing.

[INDENT][INDENT]this is a thing
[/INDENT][/INDENT]

---

### Post by urosvgd on 2016-08-31
Bashing-om, i did as you said. Now everithing is okay, thank you so much!
Hurray :)

---

### Post by Bucky Ball on 2016-08-31
Just throwing this in. While this was a good idea to fix, take note that Bashing-Oms sources are using the US mirror. This may not be the best or fastest for you, depending on where you are. Also, here in Australia, my ISP has a bunch of mirrors that are free to use, they are not metered on my internet quota. This may be the case for you.

Open Software and Updates and check the mirror. If you change it, the sources.list will be taken care of 'automagically' so it won't break anything. But it may speed up your updates. Good luck.

---

