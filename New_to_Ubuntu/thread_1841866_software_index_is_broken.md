---
title: "software index is broken"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by Pulka on 2011-09-10
Hi!


after trying to install brother printer and scanner couldn't make it work and in the process i now get this error every time i try to update, install or remove hardware.

Here's a few things i already tried. Can someone help me?

```

xxx@xxx-desktop:~$ sudo dpkg --configure -a
[sudo] password for xxx: 
xxxx@xxxx-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brscan2
0 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 171103 files and directories currently installed.)
Removing brscan2 ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/models2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
rmdir: failed to remove `/usr/local/Brother': No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
xxxx@xxxx-desktop:~$ sudo dpkg --reconfigure -a
dpkg: error: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
fields@fields-desktop:~$ sudo apt-get purge brscan2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brscan2
0 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 171103 files and directories currently installed.)
Removing brscan2 ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/models2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
rmdir: failed to remove `/usr/local/Brother': No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
fields@fields-desktop:~$ 

```

---

### Post by Pulka on 2011-09-10
No ideas?

---

### Post by Krytarik on 2011-09-10
How about this?:
```
sudo apt-get purge --force-yes brscan2
```Or this?:
```
sudo dpkg --purge --force-all brscan2
```Good luck!

---

### Post by Pulka on 2011-09-11
nothing.

got the same error messages.

---

### Post by Toz on 2011-09-11
Since:
> rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/models2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
rmdir: failed to remove `/usr/local/Brother': No such file or directory

How about:
```
sudo mkdir -p /usr/local/Brother/sane/GrayCmData/ALL
sudo mkdir -p /usr/local/Brother/sane/GrayCmData/AL
sudo mkdir -p /usr/local/Brother/sane/models2
```
then:
```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by Pulka on 2011-09-11
Thank you!

it worked!

---

### Post by Toz on 2011-09-11
Glad to hear it worked and thanks for posting back. Can you please mark this thread as solved from the Thread Tools link above?

---

