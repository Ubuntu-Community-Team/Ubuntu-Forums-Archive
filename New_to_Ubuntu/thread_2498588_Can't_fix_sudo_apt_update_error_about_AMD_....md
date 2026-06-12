---
title: "Can't fix sudo apt update error about AMD ..."
date: 2024-06-20
forum: New to Ubuntu
---

### Post by cwmoser on 2024-06-20
When I do sudo apt update I get multiple errors about:

Skipping acquire of configured file 'main/binary-AMD64/Packages' as repository 'http://us.archive.ubuntu.com/ubuntu jammy InRelease' doesn't support architecture 'AMD64'

I google this but all I find are references to i386 architecture.

Any help appreciated.

---

### Post by ActionParsnip on 2024-06-20
What is the output of
```

cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d

```

---

### Post by currentshaft on 2024-06-20
Did you modify your /etc/apt/sources file? I think you did. "AMD64" should be "amd64".

---

### Post by cwmoser on 2024-06-20
**cat -n /etc/apt/sources.list**

```

$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu-MATE 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1)]/ bionic contrib main non-free
     2	# deb cdrom:[Ubuntu-MATE 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1)]/ jammy main multiverse restricted universe
     3	
     4	
     5	
     6	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7	# newer versions of the distribution.
     8	deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
     9	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    14	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
    20	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy universe
    21	deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
    22	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
    30	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
    31	deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    32	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    40	# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    41	
    42	deb http://security.ubuntu.com/ubuntu jammy-security main restricted
    43	# deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted
    44	deb http://security.ubuntu.com/ubuntu jammy-security universe
    45	# deb-src http://security.ubuntu.com/ubuntu jammy-security universe
    46	deb http://security.ubuntu.com/ubuntu jammy-security multiverse
    47	# deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse
    48	
    49	# This system was installed using small removable media
    50	# (e.g. netinst, live or single CD). The matching "deb cdrom"
    51	# entries were disabled at the end of the installation process.
    52	# For information about how to configure apt package sources,
    53	# see the sources.list(5) manual.


```

---

### Post by cwmoser on 2024-06-20
**ls -l /etc/apt/sources.list.d**

```
$ ls -l /etc/apt/sources.list.d
total 28
-rw-r--r-- 1 root root 168 Mar 11 19:11 kdenlive-ubuntu-kdenlive-stable-jammy.list
-rw-r--r-- 1 root root 156 Jun 20 08:28 linuxuprising-ubuntu-apps-jammy.list
-rw-r--r-- 1 root root 178 Mar 11 19:11 stellarium-ubuntu-stellarium-releases-jammy.list
-rw-r--r-- 1 root root 266 Mar 11 19:11 ubuntu-esm-apps.list
-rw-r--r-- 1 root root 274 Mar 11 19:11 ubuntu-esm-infra.list
-rw-r--r-- 1 root root 160 Mar 11 19:11 ubuntuhandbook1-ubuntu-apps-jammy.list
-rw-r--r-- 1 root root  73 Mar 11 19:11 vscode.list
```

---

### Post by cwmoser on 2024-06-21
I found a fix for this ... but how did AMD64 get in there???

Here is what I found:

$ dpkg --print-foreign-architectures
i386
AMD64
$ sudo dpkg --remove-architecture AMD64
$ sudo apt update

[https://www.youtube.com/watch?v=_5r73p5kFuo](https://www.youtube.com/watch?v=_5r73p5kFuo)

---

