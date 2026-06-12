---
title: "Problem With AWK"
date: 2014-12-04
forum: Packaging and Compiling Programs
---

### Post by Nosophorus on 2014-12-04
Hi!

Some days ago I installed the newest GAWK (GNU's AWK) version (4.1.1) in my Ubuntu machine. Since that version is not available for my Ubuntu distro (Precise Pangolin 12.04 LTS), I had to install it from the source and I did that using these three commands:

01. sudo ./configure
02. sudo make
03. sudo checkinstall

I have a "Sources" folder in my "Home" folder that I created only to install softwares from source and I installed GAWK in its own subfolder in "Sources". After playing a little bit with the newest GAWK, I uninstalled it using GDebi by clicking at the ".deb" file the command "checkinstall" creates during installation.

So, I tried to revert to Ubuntu's default AWK (MAWK), but, to my surprise, now my system says it is not installed!

Any help is extremely appreciated!

Thanks!

---

### Post by schragge on 2014-12-10
I doubt it is not installed. Have you tried to call it as *mawk* (as opposite to calling just *awk*)? Most probably, just [the alternatives system](http://wiki.debian.org/DebianAlternatives) got corrupted in some way. What does the following command show?```
[color=green]$ [/color]update-alternatives --display awk
```BTW, if your system says *awk* is not installed it's normal as *awk* is a [virtual package](https://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-virtual) provided either by *mawk* or by *gawk* (or by *original-awk*). That is```
[color=green]$ [/color]dpkg -l awk
``` should show *awk* as uninstalled, but ```
[color=green]$ [/color]dpkg -l mawk
``` should show *mawk* as installed.

---

