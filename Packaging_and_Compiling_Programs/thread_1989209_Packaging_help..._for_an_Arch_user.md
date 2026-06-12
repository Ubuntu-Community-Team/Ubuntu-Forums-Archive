---
title: "Packaging help... for an Arch user"
date: 2012-05-28
forum: Packaging and Compiling Programs
---

### Post by stephenmac7 on 2012-05-28
So, I've been using Chakra/Archlinux for quite some time now but some of the software I've created requires me to repackage ffmpeg for distributions other than Arch, so I was wondering: How do I package software for Ubuntu? Is there something like an Arch PKGBUILD for Ubuntu?

---

### Post by oldos2er on 2012-05-28
I'd start with the sticky: [http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

---

### Post by stephenmac7 on 2012-05-29
> **oldos2er said:**
> I'd start with the sticky: [http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

So, there is no equivalent to a PKGBUILD in Ubuntu?

---

### Post by Bachstelze on 2012-05-29
> **stephenmac7 said:**
> So, there is no equivalent to a PKGBUILD in Ubuntu?

Not everyone here is familiar with Arch. What does PKGBUILD do?

---

### Post by stephenmac7 on 2012-05-31
Okay, I'll do my best to explain it here but there is a wiki page on it: [https://wiki.archlinux.org/index.php/PKGBUILD](https://wiki.archlinux.org/index.php/PKGBUILD)

Basically it's a text file that has information on the package (name, version, dependencies, description) and it has a list of commands on creating a folder called 'pkg' which is almost like a root system which is then compressed with the information by a script called makepkg. So, in reality the user could use makepkg and instead of installing the package file they could just use: cp -R --copy-contents pkg/* / as root and the files needed would be installed. An example is needed for clarification:

```

pkgname=todotxt-recur
pkgver=1.02
pkgrel=2
pkgdesc='Addon for todotxt in order to create recurring tasks'
arch=('i686' 'x86_64')
url='https://github.com/paulroub/todo.txt-recurring-tasks'
license=('none')
depends=('perl' 'todotxt')
source=(https://github.com/downloads/paulroub/todo.txt-recurring-tasks/Todotxt-Recur-$pkgver.tar.gz)
sha1sums=('cafdd4361a1bcb7c70a0b8259952f10e01d7e643')


build() {
  cd ${srcdir}/Todotxt-Recur-${pkgver}
  perl Makefile.PL INSTALLDIRS=vendor
  make
}


package() {
  cd ${srcdir}/Todotxt-Recur-${pkgver}
  make install DESTDIR=${pkgdir}
  rm -R $pkgdir/usr/bin
  install -Dm755 recur $pkgdir/usr/share/todotxt-addons/recur
}

```Also, it doesn't really matter what commands are in build and which are in package. It's just to help people who read the file.

---

### Post by Bachstelze on 2012-05-31
Okay, kinda similar to Gentoo ebuilds or FreeBSD ports. No, there is nothing similat for Debian/Ubuntu. You have to either use checkinstall, or go the long way as described in the packaging guide.

---

### Post by stephenmac7 on 2012-06-07
Okay... that's too bad. It's the only thing keeping me on an arch-based distro :P

---

### Post by Simian Man on 2012-06-07
> **stephenmac7 said:**
> So, I've been using Chakra/Archlinux for quite some time now but some of the software I've created requires me to repackage ffmpeg for distributions other than Arch, so I was wondering: How do I package software for Ubuntu? Is there something like an Arch PKGBUILD for Ubuntu?

I have to ask, why would it ever be a good idea to repackage ffmpeg?  You know it exposes all of its functionality via APIs.  Why would you not just distribute an application using those libraries?

---

### Post by Arand on 2012-06-26
> **stephenmac7 said:**
> So, I've been using Chakra/Archlinux for quite some time now but some of the software I've created requires me to repackage ffmpeg for distributions other than Arch, so I was wondering: How do I package software for Ubuntu? Is there something like an Arch PKGBUILD for Ubuntu?

Well, in Arch PKGBUILD holds all of the information.

In Debian it's split between several files:
```
debian/control
debian/rules
debian/packagename.install
debian/changelog
...
```

---

