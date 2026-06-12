---
title: "Options required to allow dist upgrades from a local mirror"
date: 2009-11-27
forum: Repositories &amp; Backports
---

### Post by ijosicle on 2009-11-27
Hi,

I've set up a local repository using the debian "anonftpsync" script ([http://www.debian.org/mirror/anonftpsync](http://www.debian.org/mirror/anonftpsync)). It works fine for software upgrades for the last few distributions of Ubuntu, but I would like to add the ability to doa distribution upgrade from 9.04 to 9.10. When I try to do so at the moment, I get an error that I am missing Ubuntu-minimal. In order to keep the space requirements down, I have excluded all architectures except i386 and x64. In addition, I set the following exclusions in the exclude section of the script:

EXCLUDE="\
  --exclude stable/ --exclude testing/ --exclude unstable/ \
  --exclude source/ \
  --exclude indices/ \
  --exclude universe/ \
  --exclude installer-*/ \
  --exclude *.orig.tar.gz --exclude *.diff.gz --exclude *.dsc \
  --exclude /contrib/ --exclude /non-free/ \
  --exclude *-installer-*/ \
  --exclude Archive-Update-in-Progress-* \
  --exclude ls-lR.gz \

What components will I have to include to allow a dist upgrade from the local mirror? I have used 97G so far with 122G free space remaining so I want to be careful not to exceed this. Any pointers would be very welcome.

Ijosicle

---

