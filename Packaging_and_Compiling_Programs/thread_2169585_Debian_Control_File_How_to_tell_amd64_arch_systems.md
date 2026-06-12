---
title: "Debian Control File: How to tell amd64 arch systems they depend on libudev1:i386"
date: 2013-08-22
forum: Packaging and Compiling Programs
---

### Post by marshzor on 2013-08-22
Hi All,

I'm having trouble wrapping my head around the proper way to agnosticly tell any system that is installing my .deb package that it depends on the 32 bit version of libudev. My control file looks something like this:
```
Package: my-package
Version: 1.3-16
Section: non-free/misc
Priority: optional
Architecture: i386
Installed-Size: 350
Depends: libudev1
Maintainer: me <me@me.com>
Description:
 This is my package

```

This package is intended to be able to be installed on ubuntu 12.04, 12.10 and 13.04, 32 and 64 bit arch on all 3. What I want to do is change ```
Depends: libudev1
``` to ```
Depends: libudev1:i386
``` but that doesn't seem to work the way I think it should.

Am I missing something obvious here?

I know those operating systems have libudev installed by default, but if it's a 64 bit OS it won't have the 32 bit versions of libudev that I've linked my binaries against. Anyone have any ideas as to how I can solve this without building different binaries and/or having mutliple .deb installers for different architectures?

Please let me know if there's anything important I left out or if you have any questions. Thanks in advance!

---

### Post by lukeiamyourfather on 2013-08-22
I'm not in front of a Linux machine to test this out, but I think that might be part of ia32-libs on a 64-bit system. Someone feel free to correct me if that's not the case.

---

### Post by marshzor on 2013-08-23
> **lukeiamyourfather said:**
> I'm not in front of a Linux machine to test this out, but I think that might be part of ia32-libs on a 64-bit system. Someone feel free to correct me if that's not the case.

Thanks for the response.

I had considered adding ia32-libs as a dependency but the problem is I don't want my users to have to install a 500 some odd MB package just for one library. There are other problems with this solution as well. If I were to mark the package as dependent on ia32-libs then my 32 bit users would install that package even though they don't need to since libudev is installed by default on ubuntu 12.04-13.04 (hopefully the user didn't remove it!). I really just need to make sure there is some i386 (not amd64) version of libudev installed on any machine my package is installed on.

Let me reiterate my problem and requirements here:

My program is only built for i386, if it is installed on a amd64 machine it is run in 32 bit compatibility mode and relies on the 32 bit version of certain libraries to be installed on the amd64 machine (in /lib/x86_64-linux-gnu or whatever it is) so the dependencies of my binaries can be resolved.
1. Debian package must install on 32 bit and 64 bit operating systems (same package, not a i386 version and amd64 version)
2. Debian package must install the 32 bit version of libudev0 or libudev1

Any ideas? I'm not opposed to something a bit hacky as long as it solves this problem. Oh god I can't believe I just said that.

Thanks again!

---

### Post by artbio on 2013-08-24
Try this:

```
Depends:libudev1 [i386]
```

---

### Post by artbio on 2013-08-24
> **marshzor said:**
> Thanks for the response.

I had considered adding ia32-libs as a dependency but the problem is I don't want my users to have to install a 500 some odd MB package just for one library. There are other problems with this solution as well. If I were to mark the package as dependent on ia32-libs then my 32 bit users would install that package even though they don't need to since libudev is installed by default on ubuntu 12.04-13.04 (hopefully the user didn't remove it!). I really just need to make sure there is some i386 (not amd64) version of libudev installed on any machine my package is installed on.

Let me reiterate my problem and requirements here:

My program is only built for i386, if it is installed on a amd64 machine it is run in 32 bit compatibility mode and relies on the 32 bit version of certain libraries to be installed on the amd64 machine (in /lib/x86_64-linux-gnu or whatever it is) so the dependencies of my binaries can be resolved.
1. Debian package must install on 32 bit and 64 bit operating systems (same package, not a i386 version and amd64 version)
2. Debian package must install the 32 bit version of libudev0 or libudev1

Any ideas? I'm not opposed to something a bit hacky as long as it solves this problem. Oh god I can't believe I just said that.

Thanks again!

You could try:

```
Depends: ia32-libs [amd64]
```

This way ia32-libs wouldn't be installed on an i386 system. And would be installed only on an amd64 system.

---

### Post by marshzor on 2013-08-26
> **artbio said:**
> Try this:

```
Depends:libudev1 [i386]
```


That's a good idea but I get an error from dpkg-deb when I have that line in my control file:

```

dpkg-deb: error: parsing file 'build/my-package/DEBIAN/control' near line 7 package 'my-package': `Depends' field, syntax error after reference to package `libudev0'

```

dpkg-deb version:
```

$ dpkg-deb --version
Debian `dpkg-deb' package archive backend version 1.16.10 (i386).
This is free software; see the GNU General Public License version 2 or

```

here's some info about my machine:
```

$ uname -a
Linux Latitude-E6400 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 23:12:18 UTC 2013 i686 i686 i686 GNU/Linux

```

---

### Post by marshzor on 2013-08-26
> **artbio said:**
> You could try:

```
Depends: ia32-libs [amd64]
```

This way ia32-libs wouldn't be installed on an i386 system. And would be installed only on an amd64 system.

I really really like this solution and I was definitely excited when I read your post so thanks! Unfortunately, dpkg-deb is returning an error when I attempt to add ia32-libs [amd64] to my dependency list. In fact, it just doesn't seem to like "[".

```

dpkg-deb: error: parsing file 'build/my-package/DEBIAN/control' near line 7 package 'my-package':
 `Depends' field, syntax error after reference to package `ia32-libs'

```

(Repeating this information for clarity)
dpkg-deb version:
```

$ dpkg-deb --version
Debian `dpkg-deb' package archive backend version 1.16.10 (i386).
This is free software; see the GNU General Public License version 2 or

```

here's some info about my machine:
```

$ uname -a
Linux Latitude-E6400 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 23:12:18 UTC 2013 i686 i686 i686 GNU/Linux

```

Any idea what's going on? Where did you learn about using [amd64] rather than :amd64, I've never come across that before. Is there some documentation that I'm missing?

---

### Post by marshzor on 2013-08-26
I found some useful documentation [here]("http://www.debian.org/doc/debian-policy/ch-relationships.html") and [here]("http://www.debian.org/doc/debian-policy/ch-customized-programs.html#s-arch-spec") and I changed my Architecture field to ```
Architecture: any
``` but I'm having the same exact issue. I must be doing something wrong but I can't quite track it down. Any ideas?

Edit: forgot to mention that I also tried using ```
Depends: ia32-libs [any-amd64]
``` but that didn't work either.

---

### Post by artbio on 2013-08-26
I am sorry for giving a wrong solution. I see now that you are trying to edit the control file on a ".deb" package. The syntax I was using works for the control file inside the debian folder you could use to build the actual deb files. Where there is a "Build-Depends:" field.

Now taking a look at both the i386 and the amd64 deb files for google-earth. You can download them from this webpage -> [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)
You see that there is ia32-libs on the amd64.deb file. The i386.deb file on the other hand does not have ia32-libs on the "Depends:" field of it's control file. You could try the same approach.

---

### Post by marshzor on 2013-08-27
> **artbio said:**
> I am sorry for giving a wrong solution. I see now that you are trying to edit the control file on a ".deb" package. The syntax I was using works for the control file inside the debian folder you could use to build the actual deb files. Where there is a "Build-Depends:" field.

Now taking a look at both the i386 and the amd64 deb files for google-earth. You can download them from this webpage -> [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)
You see that there is ia32-libs on the amd64.deb file. The i386.deb file on the other hand does not have ia32-libs on the "Depends:" field of it's control file. You could try the same approach.


Very interesting. Since I really want to only have one .deb file to distribute I think maybe I'll just mark my package as dependent on ia32-libs. I wonder what behavior that has on i386 machines though? I'm building a package now to try it out, I'll edit this response once I'm done.

---

### Post by artbio on 2013-08-27
If your package contains binaries you should have one package per architecture. Since there are other architectures besides i386 and amd64.

---

