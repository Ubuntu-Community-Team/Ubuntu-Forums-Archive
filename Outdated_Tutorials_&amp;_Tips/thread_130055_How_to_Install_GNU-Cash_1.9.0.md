---
title: "How to: Install GNU-Cash 1.9.0"
date: 2006-02-15
forum: Outdated Tutorials &amp; Tips
---

### Post by curtis on 2006-02-15
First of all install some of the needed packages:

```

guile-1.6-dev g-wrap libgnomeprint2.2-dev libgnomeprintui2.2-dev

```
Note: you may need one or two extra packages as I do have quiet a few dev packages already installed.

Then download the latest tarball of GNU Cash.

```

wget http://curtis.22kb.com/files/gnucash-1.9.0.tar.gz

```

Then extract it

```

tar xvzf gnucash-1.9.0.tar.gz

```

Then run ./configure
If it fails, note the package and search via apt-cache search 'package-name' then apt-get install it.

Finally make && make install it.
You could also checkinstall it if you wish.

---

