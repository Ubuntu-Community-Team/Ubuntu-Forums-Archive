---
title: "[SOLVED] dpkg Package Manager rendered useless"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by gmjs on 2008-10-31
Hello,

I wanted to install an application that requires the Qt4 libraries, so I went to install them using **aptitude** as follows:

```
**$ sudo aptitude install libqt4-dev**
```

**dpkg** downloaded the relevant packages and attempted to install them, but the installation failed at the **comerr-dev** package.  **apport** then started and suggested I filled in a bug report for the error.

As the installation was incomplete and therefore useless, I decided to remove the install.  Maybe I could try it again afterwards.  I used the following command:

```
**$ sudo aptitude purge libqt4-dev**
```

All components were removed, except for **comerr-dev**.

Now every time I try and install software using the package manager (e.g **Inkscape** as below), it fails as it tries to remove the faulty package first and can't:

```
**graham@asus:~$ sudo aptitude install inkscape**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  imagemagick{a} inkscape libblas3gf{a} libgfortran3{a} liblapack3gf{a} 
  libmagick++10{a} libwmf-bin{a} perlmagick{a} python-lxml{a} 
  python-numpy{a} python-uniconvertor{a} 
The following packages will be REMOVED:
  comerr-dev{u} 
0 packages upgraded, 11 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/22.5MB of archives. After unpacking 87.1MB will be used.
Do you want to continue? [Y/n/?] **Y**
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 100944 files and directories currently installed.)
Removing comerr-dev ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing comerr-dev (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 comerr-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

```

Is there any way I can remove **comerr-dev** so that I can use the package manager again?

Also, does anyone have an ideas as to why the **comerr-dev** package fails to install on my machine?  It's a clean install of Ubuntu 8.10 32-bit from the alternate CD with the **build-essentials** package and all updates at 30/10/2008.

Many thanks,

Graham

---

### Post by gmjs on 2008-11-01
OK, I removed the section from **/var/lib/dpkg/status** that indicates that **comerr-dev** is installed and I can now use **aptitude** again.

Now it's just a case of waiting for an 'unbroken' version of **comerr-dev**!

---

