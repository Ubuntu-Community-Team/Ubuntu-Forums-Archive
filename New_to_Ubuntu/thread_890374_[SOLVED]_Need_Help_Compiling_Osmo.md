---
title: "[SOLVED] Need Help Compiling Osmo"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by safetycopy on 2008-08-15
Hi,

I'm having some problems compiling Osmo from the 0.2.2 source. I have all the requirements and optional packages installed (as listed on the website), including the -devs. I run ./configure, then make and get this:

```
make  all-recursive
make[1]: Entering directory `/home/safetycopy/Downloads/Source/osmo-0.2.2'
Making all in src
make[2]: Entering directory `/home/safetycopy/Downloads/Source/osmo-0.2.2/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/safetycopy/Downloads/Source/osmo-0.2.2/src'
Making all in po
make[2]: Entering directory `/home/safetycopy/Downloads/Source/osmo-0.2.2/po'
/bin/bash: /usr/bin/msgfmt: No such file or directory
cs.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
de.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
es.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
fr.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
hu.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
it.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
lt.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
nl.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
pl.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
pt.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
ru.mo updated.
/bin/bash: /usr/bin/msgfmt: No such file or directory
zh.mo updated.
make[2]: Leaving directory `/home/safetycopy/Downloads/Source/osmo-0.2.2/po'
make[2]: Entering directory `/home/safetycopy/Downloads/Source/osmo-0.2.2'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/safetycopy/Downloads/Source/osmo-0.2.2'
make[1]: Leaving directory `/home/safetycopy/Downloads/Source/osmo-0.2.2'
```

---

### Post by InfinityCircuit on 2008-08-15
Are you sure you have all the dependencies installed?

```
dmoerner@ubuntu-x40:~$ apt-file search /usr/bin/msgfmt
gettext: /usr/bin/msgfmt
```

---

### Post by safetycopy on 2008-08-15
Ah thanks - that's not listed as a requirement on the website so that's where I was tripped up!

---

