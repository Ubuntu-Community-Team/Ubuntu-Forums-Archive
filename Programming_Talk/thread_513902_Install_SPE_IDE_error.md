---
title: "Install SPE IDE error"
date: 2007-07-31
forum: Programming Talk
---

### Post by craigdele on 2007-07-31
I recently install SPE  from the terminal but got the following error below. I don't know what is the cause. 

Also if I install any program using automatix2 I get a Fatal Error " An apt-based error occurred and installation was unsuccessful" The actual program does install however I think the error is based on my original SPE installation.

Can anyone help

regards

Dele



cdelehanty@dele2:~$ sudo aptitude install speReading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  python-doc python2.5-doc wx2.6-doc 
The following NEW packages will be installed:
  python-doc python2.5-doc spe wx2.6-doc 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3690kB/4205kB of archives. After unpacking 29.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/main python2.5-doc 2.5.1-0ubuntu1 [2504kB]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/main python-doc 2.5.1-0ubuntu3 [9786B]
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/universe wx2.6-doc 2.6.3.2.1.5ubuntu6 [1176kB]
Fetched 3690kB in 28s (128kB/s)                                                 
Selecting previously deselected package python2.5-doc.
(Reading database ... 137971 files and directories currently installed.)
Unpacking python2.5-doc (from .../python2.5-doc_2.5.1-0ubuntu1_all.deb) ...
Selecting previously deselected package python-doc.
Unpacking python-doc (from .../python-doc_2.5.1-0ubuntu3_all.deb) ...
Selecting previously deselected package spe.
Unpacking spe (from .../spe_0.8.2a+repack-1_all.deb) ...
Selecting previously deselected package wx2.6-doc.
Unpacking wx2.6-doc (from .../wx2.6-doc_2.6.3.2.1.5ubuntu6_all.deb) ...
Setting up python2.5-doc (2.5.1-0ubuntu1) ...

Setting up python-doc (2.5.1-0ubuntu3) ...
Setting up spe (0.8.2a+repack-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
dpkg: error processing spe (--configure):
 subprocess post-installation script returned error exit status 1
Setting up wx2.6-doc (2.6.3.2.1.5ubuntu6) ...

Errors were encountered while processing:
 spe
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up spe (0.8.2a+repack-1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/_spe/doc
dpkg: error processing spe (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 spe

---

