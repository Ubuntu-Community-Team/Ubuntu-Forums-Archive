---
title: "ERROR message"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by monolux on 2008-07-17
> monolux@monolux-desktop:~$ sudo apt-get install rtorrent[sudo] password for monolux:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtorrent is already the newest version.
The following packages will be REMOVED:
  epiphany-browser-data gnome-themes-extras
0 upgraded, 0 newly installed, 2 to remove and 944 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 27.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131378 files and directories currently installed.)
Removing epiphany-browser-data ...
/usr/share/icons/HighContrastLargePrint is not a directory
dpkg: error processing epiphany-browser-data (--remove):
 subprocess post-removal script returned error exit status 2
Removing gnome-themes-extras ...
/usr/share/icons/Foxtrot is not a directory
dpkg: error processing gnome-themes-extras (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 epiphany-browser-data
 gnome-themes-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)

I keep on getting this error message while trying to install rtorrent. Any clue on how to solve it?

---

### Post by sdennie on 2008-07-17
Try:

```

sudo apt-get install -f

```

or

```

sudo dpkg --configure -a

```

---

### Post by monolux on 2008-07-17
nope didn't work.

---

### Post by Inxsible on 2008-07-17
> **monolux said:**
> nope didn't work.
When you say it didnt work...how do you mean ?

did it give any errors? any response at all? Passing on the details to us, helps us in helping you.


BTW : rTorrent is NOT your problem. If you read the output ..it says: rtorrent is already the newest version.

You only have some broken packages - probably when you removed something without thinking about the dependencies.

---

### Post by monolux on 2008-07-17
So how do I fix the broken packages?

---

