---
title: "2 pkgs claim ea. other as dependencies?!?"
date: 2006-05-14
forum: Repositories &amp; Backports
---

### Post by Bunkai on 2006-05-14
```
dan@ze4200:~/MyPkgs/temp$ sudo dpkg -i libstdc++*.deb
Password:
Selecting previously deselected package libstdc++6-4.0-dev.
(Reading database ... 64909 files and directories currently installed.)
Unpacking libstdc++6-4.0-dev (from libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Preparing to replace libstdc++6-4.0-doc 4.0.1-4ubuntu9 (using libstdc++6-4.0-doc_4.0.1-4ubuntu9_all.deb) ...
Unpacking replacement libstdc++6-4.0-doc ...
dpkg: dependency problems prevent configuration of libstdc++6-4.0-dev:
 [COLOR="blue"]libstdc++6-4.0-dev depends on g++-4.0 (= 4.0.1-4ubuntu9); however:
  Package g++-4.0 is not configured yet.[/COLOR]
dpkg: error processing libstdc++6-4.0-dev (--install):
 dependency problems - leaving unconfigured
Setting up libstdc++6-4.0-doc (4.0.1-4ubuntu9) ...

Errors were encountered while processing:
 libstdc++6-4.0-dev
dan@ze4200:~/MyPkgs/temp$ sudo dpkg -i g++-4*.deb
(Reading database ... 65186 files and directories currently installed.)
Preparing to replace g++-4.0 4.0.1-4ubuntu9 (using g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Unpacking replacement g++-4.0 ...
dpkg: dependency problems prevent configuration of g++-4.0:
 [COLOR="Blue"]g++-4.0 depends on libstdc++6-4.0-dev (= 4.0.1-4ubuntu9); however:
  Package libstdc++6-4.0-dev is not configured yet.[/COLOR]
dpkg: error processing g++-4.0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-4.0
dan@ze4200:~/MyPkgs/temp$
```
Can anyone explain how to get around this impass?
Thanks.

---

### Post by gborzi on 2006-05-14
Actually the packages were installed but not configured. You can uninstall them and then try to install both with the same command, i.e.
> sudo dpkg -r libstdc++6-4.0-dev g++-4.0
sudo dpkg -i g++-4*.deb libstdc++*.deb
however the "regular" way to install packages in the repositories is
> sudo apt-get install libstdc++6-4.0-dev g++-4.0
and apt will take care of dependencies. dpkg is used only to install packages not in the repositories or when you cannot access directly the repositories from internet.
In this case you have to download the packages from another computer, put them in a storage medium, bring them to your ubuntu computer, use dpkg on all of them and pray there are not missing dependencies.

---

### Post by Bunkai on 2006-05-14
[QUOTE=gborzi]dpkg is used only to install packages not in the repositories or when you cannot access directly the repositories from internet.[/QUOTE]
Yes that's why I'm going through all of this - to get an Internet connection through my winmodem I need to build from a tarball. Thanks for the suggestion, I'll give it a whirl.

---

### Post by Bunkai on 2006-05-14
gborzi,
It seems to have worked like a charm. Big thumbs up!
Thanks.

---

