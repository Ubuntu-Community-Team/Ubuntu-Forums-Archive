---
title: "How to see Vendors for installed packages"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by marc46 on 2014-12-29
I've been tasked with looking at some ubuntu servers and determining vendors packages are installed on these servers. 

I used:   dpkg --get-selections | grep -v deinstall

This gave me a list of all packages installed, but did not show any vendor information. 
Is there a way to do this on ubuntu without installing rpm?[FONT=Ubuntu Mono]
[/FONT]

---

### Post by Holger_Gehrke on 2014-12-29
You might want to look at the manual page for dpkg-query, especially the --show command and the --showformat option. But there doesn't seem to be anything like a 'Vendor' in the field available only a 'Maintainer'. Installing rpm would be worse than useless, a package manager is a **very** basic part of the system, having two of them is a recipe for chaos. Never mind that rpm wouldn't know a thing about the packages, since it cant read and understand a debian package database - just like dpkg can't read a Red Hat package db.

You could of course look in Synaptic. Switch to view by Origin and look at packages from local files or from Non-Free (restricted or and parts of Multiverse) sources. If you then set a filter to only show you the installed packages, you're quite a bit closer to your goal ...

---

### Post by schragge on 2014-12-29
TBH there **is** *Origin* field in dpkg-query format string, but it doesn't mean the same as Origin in Synaptic and is mostly useless. Try
```
dpkg-query -Wf'${Package}:${Origin}\n'|grep :debian$
``` and you'll see what I mean. To see all available values for this field (currently only *debian*), run
```
grep ^Origin: /var/lib/dpkg/status|sort -u
```

OTH, the search term ~O in aptitude is much more useful. E.g. try
```

sudo apt-get install aptitude
aptitude search -F '%p %t %20s' '!~OUbuntu!~v'

```
To see what values are available for ~O, run
```

grep -h ^Origin: /var/lib/apt/lists/*_Release|sort -u

```
There's also such thing as default or current distribution vendor. This is what you get shown with
```

dpkg-vendor --query Vendor

```
With this information, the aptitude command above that searches for packages not from current vendor could be modified to work on any Debian-based distribution:
```

aptitude -F '%p %t %20s' search '!~v!~O'"`dpkg-vendor --query Vendor`"

```

 [post=12568872]Here[/post] and [post=12583941]here[/post] I once tried to filter packages from now defunct medibuntu repository.

---

