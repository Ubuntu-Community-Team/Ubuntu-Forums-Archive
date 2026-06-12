---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-10-12
forum: New to Ubuntu
---

### Post by asaadirfans on 2015-10-12
[COLOR=#DD1144][FONT=Menlo]I'm using ubunti 12.05.5 and when i try to do this:

sudo apt-get -f install


I get the following error:

[/FONT][/COLOR]asaad@VAIO:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libopenni-nite-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 579300 files and directories currently installed.)
Removing libopenni-nite-dev ...
Failed: Error!
dpkg: error processing libopenni-nite-dev (--remove):
 subprocess installed pre-removal script returned error exit status 255
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libopenni-nite-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
asaad@VAIO:~$ 



Any help would be really appreciated.

---

### Post by lisati on 2015-10-12
Duplicate of [http://ubuntuforums.org/showthread.php?t=2298597](http://ubuntuforums.org/showthread.php?t=2298597) closed.

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

