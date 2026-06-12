---
title: "compare multiple files"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by cacs on 2011-11-04
Hi.
There a way to compare several files within a folder to find repeated ones?
ty

---

### Post by Lars Noodén on 2011-11-04
If I recall correctly you can use [rdiff](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rdiff.1.html) to compare multiple files, but it won't necessarily find duplicated.  

One way would be to write a script in perl or another scripting language to genereate MD5 or SHA checksums and report duplicates.

---

### Post by Frogs Hair on 2011-11-04
I use Gloobus Preview , it is in the software center in 11.10 and it came with the Elementary Nautilus PPA in 11.04 .

To get it working easily in 11.10 see the link .[http://ubuntuguide.net/gloobus-preview-updated-with-ubuntu-11-10-nautilus-3-2-support](http://ubuntuguide.net/gloobus-preview-updated-with-ubuntu-11-10-nautilus-3-2-support)

---

### Post by cacs on 2011-11-13
> **cacs said:**
> Hi.
There a way to compare several files within a folder to find repeated ones?
ty

Ty all.

I meant to look for duplicated files. I already find a program for windows and use it under wine. Is there a good ubuntu program for this purpose?

---

### Post by sanderd17 on 2011-11-13
fdupes looks very good to me: [http://packages.ubuntu.com/en/natty/fdupes](http://packages.ubuntu.com/en/natty/fdupes)

It uses md5sums to compare the files, and it reports a list of equal files.

I hope it's not a problem that it's a command line tool.

---

### Post by alex2399 on 2011-11-13
I can recommend FSlint and Beyond Compare (30 day no restrictions trial) within Wine.

FSlint checks duplicate content and duplicate filenames amongst others. Beyond Compare is good for checking and viewing similar files and directories.

---

### Post by cacs on 2011-11-18
> **sanderd17 said:**
> fdupes looks very good to me: [http://packages.ubuntu.com/en/natty/fdupes](http://packages.ubuntu.com/en/natty/fdupes)

It uses md5sums to compare the files, and it reports a list of equal files.

I hope it's not a problem that it's a command line tool.


Ty. No problem with the CL, but a nice looking gui would be nice! :)

---

### Post by cacs on 2011-11-18
> **alex2399 said:**
> I can recommend FSlint and Beyond Compare (30 day no restrictions trial) within Wine.

FSlint checks duplicate content and duplicate filenames amongst others. Beyond Compare is good for checking and viewing similar files and directories.


Ty, i got a free one, but i want one for ubuntu not using wine! :)

---

