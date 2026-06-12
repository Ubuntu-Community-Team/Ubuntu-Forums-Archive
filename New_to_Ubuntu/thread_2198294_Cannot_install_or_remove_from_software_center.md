---
title: "Cannot install or remove from software center"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by lunatunes on 2014-01-08
First of all, Im a new linux user here so that is my defense for messing up my software center...lol :(
I installed openoffice through the terminal then tried uninstalling it by eventually removing files
in the root directory via terminal. Once uninstalled I installed Libreoffice. It's installed but it doesnt
work now :(

Now if I try to remove or install anything, I get:
"Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

here is what comes up....

> rand@rand-desktop:~$ sudo apt-get install -f
[sudo] password for rand: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  evolution-common hyphen-en-us kde-l10n-engb libevolution libexempi3
  libgpgme++2 libgrantlee-core0 libgrantlee-gui0 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libkdgantt2-0 libpostproc52
  libpst4 libqgpgme1 libytnef0 linux-headers-3.11.0-12
  linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic
  linux-image-extra-3.11.0-12-generic mythes-en-au openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
18 not fully installed or removed.
Need to get 0 B/27.7 MB of archives.
After this operation, 76.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? ^Crand@rand-desktop:~$ 

Could someone please help me get my linux back?  I spent a good part of a week
learning how to get it all set up and my files and things transferred over from windows,
Reinstalling xubuntu and starting all over again would be.....well, I'd probably cry!

Thanks,
Rand

---

### Post by xeonix on 2014-01-08
I don't find anything wrong there, just hit enter button at last line, instead of ^c

---

### Post by mark65ak on 2014-01-08
you never answered the Y/n question with Y for yes you want to continue.

---

### Post by lunatunes on 2014-01-08
Oops, forgot to copy the rest :)

```
Do you want to continue [Y/n]? y
(Reading database ... 239936 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.4~rc2-0ubuntu1~saucy1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.4~rc2-0ubuntu1~saucy1~ppa1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
                                                              rmdir: failed to remove ‘/var/lib/libreoffice/share/prereg/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/share/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/program/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.4~rc2-0ubuntu1~saucy1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rand@rand-desktop:~$ 

```

---

### Post by ibjsb4 on 2014-01-08
Try cleaning out your system.

```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by QIII on 2014-01-08
Hello!

Let's take a step back here.

What, exactly, did you do to install OpenOffice initially?

---

### Post by Impavidus on 2014-01-08
```
Do you want to continue [Y/n]? y
(Reading database ... 239936 files and directories currently installed.)
Unpacking **libreoffice-common** (from .../libreoffice-common_1%3a4.1.4~rc2-0ubuntu1~saucy1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.4~rc2-0ubuntu1~saucy1~ppa1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package **openoffice-debian-menus** 4.0-9714
No apport report written because MaxReports is reached already
(...)

```
There is a conflict between a package belonging to libreoffice and package remaining from openoffice. You didn't state how you installed openoffice, but apparently throught the package manager, which is the right way. However, you didn't uninstall it the right way, so now the package manager thinks you still have openoffice installed and it refuses to install the conflicting libreoffice. The package openoffice-debian-menus (and probably some other packages belonging to openoffice) have to be properly uninstalled before you can install libreoffice.

---

### Post by lunatunes on 2014-01-08
Thanks everyone for the help!

Openoffice was not in the software center so I installed it via the terminal
by following this thread: 

[http://askubuntu.com/questions/116590/how-do-i-install-openoffice-org-instead-of-libreoffice](http://askubuntu.com/questions/116590/how-do-i-install-openoffice-org-instead-of-libreoffice)


Rand

---

### Post by lunatunes on 2014-01-08
Ipavidus:  I used cat fish file search to find any "openoffice-debian-menu"  files and 
found 5 of them. I removed them using sudo rm -rf (name of package).

It worked!!!   Libre office is up and running and the software center is working :)
Thanks so much!

I found most of the debian files in /var/lib/dpkg/info.  There are about 100 other
openoffice files inside the "info" folder. 

 Should I remove those also?

Rand

---

### Post by Impavidus on 2014-01-08
I assume you used the PPA? Then removing openoffice with **sudo rm <files>** caused your problem in the first place. Packages should be uninstalled using **sudo apt-get purge <package>**, else the package manager will get confused.

---

