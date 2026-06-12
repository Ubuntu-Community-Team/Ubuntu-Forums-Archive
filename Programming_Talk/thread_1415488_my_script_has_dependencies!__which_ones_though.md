---
title: "my script has dependencies!  which ones though?"
date: 2010-02-24
forum: Programming Talk
---

### Post by outleradam on 2010-02-24
Ok, so I don't really understand what I have to do here.  If people from other distributions of linux want to use my script, they need to have dependencies..  What is a dependency amongst this list?   Most of it comes with bash.  When I write my dependency list, what should be included?  

GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)
sed GNU sed version 4.2.1
mysql  Ver 14.14 Distrib 5.1.37, for debian-linux-gnu (i486) using  EditLine wrapper
replace  Ver 1.4 for debian-linux-gnu at i486
tr (GNU coreutils) 7.4
tail (GNU coreutils) 7.4
rm (GNU coreutils) 7.4
mv (GNU coreutils) 7.4
mkdir (GNU coreutils) 7.4
expr (GNU coreutils) 7.4
date (GNU coreutils) 7.4
basename (GNU coreutils) 7.4
cGNU grep 2.5.4
ut (GNU coreutils) 7.4
notify-send 0.4.5
agrep -V This is agrep version 3.0, 1994.
curl 7.19.5 (i486-pc-linux-gnu) libcurl/7.19.5 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.15

---

### Post by falconindy on 2010-02-25
> **outleradam said:**
> Ok, so I don't really understand what I have to do here.  If people from other distributions of linux want to use my script, they need to have dependencies..  What is a dependency amongst this list?   Most of it comes with bash.  When I write my dependency list, what should be included?  

GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)
sed GNU sed version 4.2.1
mysql  Ver 14.14 Distrib 5.1.37, for debian-linux-gnu (i486) using  EditLine wrapper
replace  Ver 1.4 for debian-linux-gnu at i486
tr (GNU coreutils) 7.4
tail (GNU coreutils) 7.4
rm (GNU coreutils) 7.4
mv (GNU coreutils) 7.4
mkdir (GNU coreutils) 7.4
expr (GNU coreutils) 7.4
date (GNU coreutils) 7.4
basename (GNU coreutils) 7.4
cGNU grep 2.5.4
ut (GNU coreutils) 7.4
notify-send 0.4.5
agrep -V This is agrep version 3.0, 1994.
curl 7.19.5 (i486-pc-linux-gnu) libcurl/7.19.5 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.15
Anything in coreutils can be safely ignored. Sed can likely be skipped as well. The rest of it needs to be mentioned as its either non-standard or can be flavored.

Other comments:
* Did you mean 'cut' instead of 'ut'? 
* I absolutely cannot believe that you need 2 versions of grep for a single script.
* notify-send is part of libnotify.
* Somewhat of a non-issue, but basename is unnecessary provided in Bash4. `basename $file` is the same as `echo ${file##*/}`.
* If you really want to cut back on dependencies, aim for POSIX compliance. Rename could be replaced by sed.

---

