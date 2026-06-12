---
title: "i can install firefox but cant install mozilla?"
date: 2005-01-17
forum: Repositories &amp; Backports
---

### Post by T31 on 2005-01-17
####### Im trying to install mozilla with synaptic but i get this msg all the time even when i already have libnspr4 2:1.7.3-5
_____________________________________________________
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences

mozilla-browser:
  Depends: libnspr4 (=2:1.7.3-1ubuntu1) but 2:1.7.3-5 is to be installed
__________________________________________________________

###### Ive checked and everything looks ok this is my sources.list:



deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# ubuntu guia inicio 1
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# ubuntu guia final 1

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

# ubuntu guia inicio 2

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
# ubuntu guia final 2

# beware: this can break your warty installation if not pinned properly!
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

# from hoary firefox 1.0 y k3b 0.11.17
deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe 
________________________________________________________________________

######### and this my preferences file

Package: *
Pin: release a=warty
Pin-Priority: 600

Package: *
Pin: release a=hoary
Pin-Priority: 10

Package: *
  Pin: release o=Christian Marillat
  Pin-Priority: 1




############ please help

---

### Post by rudiz on 2005-01-20
sudo apt-get install mozilla-browser

---

### Post by mendicant on 2005-01-20
[QUOTE=T31]####### Im trying to install mozilla with synaptic but i get this msg all the time even when i already have libnspr4 2:1.7.3-5
_____________________________________________________
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences

mozilla-browser:
  Depends: libnspr4 (=2:1.7.3-1ubuntu1) but 2:1.7.3-5 is to be installed
__________________________________________________________


############ please help[/QUOTE]

Presumably, some entry in your sources list wants to upgrade libnspr4 to 1.7.3-5, which breaks mozilla-browser, since it requires the exact version 1.7.3-1ubuntu1.  You can hold ('=' in aptitude) libnspr4 to 1.7.3-1ubuntu1, or remove the offending entry from your sources.list.  Be aware if you hold it, that it will stay held until you manually select it to be updated.  Holding it may prevent other packages from installing, if they require > 1.7.3-1.

mendicant.

---

### Post by mendicant on 2005-01-20
Reading a little more closely, you already have 1.7.3-5 installed, which means that you can't install a package (like mozilla-browser) that depends on a version < 1.7.3-5.  You can downgrade it, and possibly break other packages, or install a version of mozilla-browser that requires 1.7.3-5 of nspr.  I'm not sure which repository gave you 1.7.3-5 nspr, but it wasn't warty or hoary.

---

