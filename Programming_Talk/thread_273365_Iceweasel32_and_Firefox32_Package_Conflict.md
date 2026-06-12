---
title: "Iceweasel32 and Firefox32 Package Conflict"
date: 2006-10-07
forum: Programming Talk
---

### Post by fatsheep on 2006-10-07
When I have firefox32 already installed and I try to install iceweasel I get this:


> 
Selecting previously deselected package iceweasel32.
(Reading database ... 160115 files and directories currently installed.)
Unpacking iceweasel32 (from .../iceweasel-1.5.0.4-g1-amd64.deb) ...
dpkg: error processing /home/fatsheep/Desktop/Downloads/iceweasel-1.5.0.4-g1-amd64.deb (--install):
[B] trying to overwrite `/etc/pango32/pangorc', which is also in package firefox32
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/B]


And when I already have Iceweasel32 installed and I try to install Firefox32 I get this:

> (Reading database ... 80636 files and directories currently installed.)
Unpacking firefox32 (from .../firefox32-1.5.0.7_amd64.deb) ...
dpkg: error processing [B]/home/ubuntu/Desktop/ffinstall/firefox32-1.5.0.7_amd64.de b (--install):
 trying to overwrite `/etc/pango32/pangorc', which is also in package iceweasel3 2[/B]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/ubuntu/Desktop/ffinstall/firefox32-1.5.0.7_amd64.deb
chmod: cannot access `/usr/local/bin/firefox32': No such file or directory


#1  How could I force the package in and overwrite /etc/pango32/pangorc?  
#2  If /etc/pango32/pangorc differs in firefox32 and Iceweasel32 is there a nother way I could resolve the conflict?

---

### Post by po0f on 2006-10-07
fatsheep,

Try just moving pangorc to a different file and installing the second package.  After you install, diff the files to see if there are any major differences between them:
```
# mv /etc/pango32/pangorc /etc/pango32/pangorc.bak
(install the second package)
# diff /etc/pango32/pangorc /etc/pango32/pangorc.bak
```

IIRC, in the output of diff, the first file's contents will be preceded with << and the second file's contents will be preceded with >>.

---

### Post by fatsheep on 2006-10-08
I tried doing what you said and I am still getting this error:

> (Reading database ... 83068 files and directories currently installed.)
Unpacking firefox32 (from firefox32-1.5.0.7_amd64.deb) ...
dpkg: error processing firefox32-1.5.0.7_amd64.deb (--install):
** trying to overwrite `/etc/pango32/pangorc', which is also in package iceweasel3 2**
dpkg-deb: subprocess paste killed by signal (Broken pipe)


I have double checked and /etc/pango32/pangorc does not exist.  I guess this problem is rooted in the package database. ](*,)

---

