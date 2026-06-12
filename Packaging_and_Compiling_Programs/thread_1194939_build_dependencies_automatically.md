---
title: "build dependencies automatically"
date: 2009-06-23
forum: Packaging and Compiling Programs
---

### Post by rosenth on 2009-06-23
hi
[here]("http://ubuntuforums.org/showthread.php?t=51003") is a script:
```
 strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done
```
that shows dependecies needed to compile source code. is there a more convinent way to feed output of this script directly into 
```
sudo apt-get install
```
command. and install them automatically

---

### Post by regala on 2009-06-23
> **rosenth said:**
> hi
[here]("http://ubuntuforums.org/showthread.php?t=51003") is a script:
```
 strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done
```
that shows dependecies needed to compile source code. is there a more convinent way to feed output of this script directly into 
```
sudo apt-get install
```
command. and install them automatically

sudo apt-get build-dep <package-name>

it looks in the debian/control file and install all Build-Depends: packages.

---

### Post by rosenth on 2009-06-23
but its not a package. its a source code that i need to satisfy its dependencies while running ./configure

---

### Post by blackxored on 2009-06-23
I don't know if its your script what I've ran in the past. But I'll answer anyway: this script won't show you all dependencies, right? It will stop after first configure error?

---

### Post by rosenth on 2009-06-24
yes. it stop for first error.
but what u suggest? how can i extract dependency checks from configure file?

---

