---
title: "dependency is not satisfiable"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by mikee2 on 2014-03-18
I am a new user to Ubuntu and seeking for help on installing a mod fro Nautilus here[: https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/]("https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/")  I am running 12.04 on 32 bit machine. The instructions were to download teh Deb file and follow the inrtutions, but when i click on that file it opens the Software Centre and then says:

dependency is not satisfiable

Do I need to extract and compile all  these files or? I am not sure what I am doing wrong. 
I downloaded the **[nautiluspatch_v3.4.2-0ubuntu8-1_i386.deb]("https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu8-1_i386.deb")**  file fromthe top. Do I need all the files?  [INDENT]   

 [/INDENT]
(udpate looks like there is a bug maybe?)

[https://bugs.launchpad.net/nautiluspatchtogglelocationbar/+bug/1098469](https://bugs.launchpad.net/nautiluspatchtogglelocationbar/+bug/1098469)

is there a workaround for this? this seems so complicated for just getting simple navigation buttons!

---

### Post by Vladlenin5000 on 2014-03-18
If your Nautilus version is anything but 3.4.2 it won't work. The current stable version is 3.8.2.

---

### Post by Impavidus on 2014-03-18
```
$ dpkg-deb -f nautiluspatch_v3.4.2-0ubuntu8-1_i386.deb 
Package: nautiluspatch
Version: 3.4.2-0ubuntu8-1
Section: base
Installed-Size: 6
Priority: optional
Architecture: i386
[B]Depends: bash
Pre-Depends: bash, zenity, zenity-common, awk, nautilus(>=1:3.4.2-0ubuntu8), nautilus(<<1:3.4.2-0ubuntu9)[/B]
Maintainer: Raya Christian <kirby_33@hotmail.fr>
Description: Patch for Nautilus file manager.
Homepage: http://ubuntuforums.org
```
On my system (12.04):```
bash:          4.2-2ubuntu2.1
zenity:        3.4.0-0ubuntu4
zenity-common: 3.4.0-0ubuntu4
awk:           not available, although gawk (GNU AWK) is, version 1:3.1.8+dfsg-0.1ubuntu1
nautilus:      1:3.4.2-0ubuntu9
```So there is a problem with the nautilus version. And with awk, it seems.

---

