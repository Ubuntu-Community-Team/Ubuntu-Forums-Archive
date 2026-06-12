---
title: "Compile software debian way"
date: 2012-01-16
forum: Packaging and Compiling Programs
---

### Post by jlazkano on 2012-01-16
Hello all, I am trying to compile and install mythstream software on a Ubuntu OS. This is a plugin of MythTV to play online streams. I found a recent verion on debian-multimedia repository. I have 11.04 version of Ubuntu with this kernel:

```
$ uname -a
Linux wl183097 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i686 i386 GNU/Linux
```

I install the dependencies:

```
sudo apt-get install debhelper libmyth-dev fftw3-dev libqt4-dev libexpat1-dev quilt ccache
```

Download debian-multimedia files:

```
wget http://debian-multimedia.org/pool/main/m/mythstream/mythstream_0.21+svn-r21640-0.4.diff.gz
wget http://debian-multimedia.org/pool/main/m/mythstream/mythstream_0.21+svn-r21640-0.4.dsc
wget http://debian-multimedia.org/pool/main/m/mythstream/mythstream_0.21+svn-r21640.orig.tar.gz
```

Compile debian way:

```
dpkg-source -x mythstream_0.21+svn-r21640-0.4.dsc
cd mythstream-0.21+svn-r21640/
dpkg-buildpackage -us -uc -b
```

Now I have the deb package: mythstream_0.21+svn-r21640-0.4_i386.deb

The problem is when I try to install the package:

```
$ sudo dpkg -i mythstream_0.21+svn-r21640-0.4_i386.deb 
Selecting previously deselected package mythstream.
dpkg: regarding mythstream_0.21+svn-r21640-0.4_i386.deb containing mythstream:
 mythtv-frontend conflicts with mythstream (<< 0.21.0)
  mythstream (version 0.21+svn-r21640-0.4) is to be installed.
dpkg: error processing mythstream_0.21+svn-r21640-0.4_i386.deb (--install):
 conflicting packages - not installing mythstream
Errors were encountered while processing:
 mythstream_0.21+svn-r21640-0.4_i386.deb
```

I have installed mythtv-frontend and it works great.

How could I install the mythstream software?

I will apreciate any help.

Thanks and best regards.

---

### Post by oldos2er on 2012-01-16
Moved to Packaging and Compiling Programs.

---

### Post by Bachstelze on 2012-01-16
You are trying to install mythstream from mythtv 0.21 but your installed version of mythtv is probably higher. You need to install mythstream from the version of mythtv that corresponds to the one currently installed.

---

