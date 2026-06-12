---
title: "Getting a user's selected apt-get mirror"
date: 2007-12-19
forum: Programming Talk
---

### Post by Cappy on 2007-12-19
I need like to get the mirror a user uses.
Currently I have
```
if [ -f "/etc/apt/sources.list" ]; then
        mirror=`grep -m 1 "^deb" /etc/apt/sources.list | cut -f2 -d ' '`
    elif [ -f "/etc/apt/sources.lst" ]; then
        mirror=`grep -m 1 "^deb" /etc/apt/sources.lst | cut -f2 -d ' '`
    else
        echo "no /etc/apt/sources.list or /etc/apt/sources.lst"
        mirror="http://mirrors.kernel.org/ubuntu/"
    fi
    echo "Using mirror $mirror" 

```
but this seems prone to error because something like medibuntu could have the first place in the /etc/apt/sources.list file.

Does anyone know a better way to achieve this?

---

### Post by geirha on 2007-12-19
The mirror can also be specified in a different file in /etc/apt/sources.list.d/ , so a better way would be to use an apt-command that parses all these files for you, and use that output to find the url for the main repository. I don't have too much knowledge about apt, but "apt-cache policy" seems to give out usable output. So maybe something like this?
```
apt-cache policy|grep -o 'http://.*gutsy/main Packages' | sed 's|^[0-9 ]*\(http://[^ ]\+\) gutsy/main Packages|\1|'
```

---

### Post by Cappy on 2007-12-19
Excellent; Thank you!

```
$ apt-cache policy libqt4-core
libqt4-core:
  Installed: 4.3.2-0ubuntu3.1
  Candidate: 4.3.2-0ubuntu3.1
  Version table:
 *** 4.3.2-0ubuntu3.1 0
        500 ftp://ftp.gtlib.gatech.edu gutsy-updates/main Packages
        100 /var/lib/dpkg/status
     4.3.2-0ubuntu3 0
        500 ftp://ftp.gtlib.gatech.edu gutsy/main Packages
        500 http://archive.ubuntu.com gutsy/main Packages

```
brings me 50% closer to a perfect solution.

```
apt-cache policy $package | grep -o -m 1 '\(http\|ftp\)[^ ]*'
```
will give me
> [ftp://ftp.gtlib.gatech.edu](ftp://ftp.gtlib.gatech.edu)
which I could then grep for in the sources.list because I still need to know if the mirror uses /ubuntu/ or /pub/ubuntu or /mirrors/ubuntu/, etc. for the directory.

---

