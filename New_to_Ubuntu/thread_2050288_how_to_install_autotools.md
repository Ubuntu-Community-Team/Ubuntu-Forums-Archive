---
title: "how to install autotools"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by mark allyn on 2012-08-30
Hello everyone,
 
I am tying to install autotools on my 12.04 machine.  I enter 'sudo apt-get install automake'  and the system informs me that it isn't available.  It suggests places that it can be found, but when I try to apt-get them, they aren't around either.  Seems hard to believe that it wouldn't be part of the 12.04 distro....I'm obviously new (very) to Ubuntu.  I searched the internet and this forum but drew blanks on the question.
 
Thanks,
Mark Allyn

---

### Post by steeldriver on 2012-08-30
I'm not sure there is an actual autotools metapackage - I think there are 2 separate packages (autoconf and automake) but if you install autoconf then automake is added as a dependency

I just did this yesterday on my 12.04 box fwiw

EDIT: my bad, it's the other way around (although my bash history confirms I actually installed autoconf - so I must have accepted the recommend somehow)

```

$ apt-cache depends autoconf
autoconf
  Depends: perl
  Depends: m4
  Depends: debianutils
  Suggests: autoconf2.13
  Suggests: autoconf-archive
  Suggests: gnu-standards
  Suggests: autoconf-doc
  Suggests: libtool
  Suggests: gettext
 |Recommends: automake
  Recommends: <automaken>
    automake
    automake1.10
    automake1.7
    automake1.9
  Conflicts: autoconf2.13
  Conflicts: gettext
  Conflicts: pkg-config
$ apt-cache depends automake
automake
  Depends: autoconf
  Depends: autotools-dev
 |Depends: dpkg
  Depends: install-info
  Conflicts: automake
  Conflicts: <automake1.10-doc>
  Conflicts: <automake1.5>
  Conflicts: <automake1.6>
$ 
```

---

### Post by mikechant on 2012-08-30
I would recommend using the search facility in the 'Synaptic' gui package manager to search for automake, this might be a package naming issue.

If synaptic isn't installed (not sure if it was removed for default install in 12.04) you can install it from the software center or via 'sudo apt-get install synaptic'.

I nearly always use synaptic to install things, you can see related packages etc. with the search facility which is often useful.

---

### Post by mark allyn on 2012-08-31
Hello everyone,
 
I downloaded three tarballs from GNU.org:  M4, Autoconfig, and Automake.  I decompressed all three.  I went thru the ./configure, make, make install process for M4, then Autoconfig, and then Automake.  All went well.  The tools work.
 
I still don't understand why they are not part of the 12.04 Ubuntu distro.  I thought they were sort of foundational for exchanging OS code.
 
Cheers,
Mark

---

### Post by Frogs Hair on 2012-08-31
I find automake in the 12.04 synaptic package manager.

---

