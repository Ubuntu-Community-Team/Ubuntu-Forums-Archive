---
title: "glibc and libstdc++ docs with devhelp?"
date: 2008-06-23
forum: Programming Talk
---

### Post by not_surt on 2008-06-23
I'm just wondering if there's a straightforward way to get access to the glibc and libstdc++ docs through devhelp.

I've got the glibc-doc and libstdc++6-4.2-doc packages installed but nothing relevant shows up in devhelp.

Any ideas?

---

### Post by glasper on 2008-07-08
Although both of those doc packages come in html versions, nobody appears to have bothered to package them in a way compatible with devhelp.

There is an old version of the glibc docs in devhelp format for debian sarge at [http://packages.debian.org/sarge/devhelp-book-glibc](http://packages.debian.org/sarge/devhelp-book-glibc).  I can confirm that this is compatible with Ubuntu: download it manuallly and install it with dpkg --install.  I am still looking for the standard C++ library docs in devhelp format.

---

### Post by not_surt on 2008-07-16
Sweet, works nicely.

---

### Post by SwedishWings on 2008-11-06
Old thread... 

I tried to download devhelp-book-glibc from the link above, but it has been removed. Any ideas where i can find it?

Thanks,
Mike

---

### Post by SwedishWings on 2009-06-10
Found it at: [http://ftp3.nrc.ca/debian-archive/pool/main/d/devhelp-books/devhelp-book-glibc_0.5_all.deb](http://ftp3.nrc.ca/debian-archive/pool/main/d/devhelp-books/devhelp-book-glibc_0.5_all.deb)

Some links on this page still works: [http://archive.debian.net/sarge/all/devhelp-book-glibc/download](http://archive.debian.net/sarge/all/devhelp-book-glibc/download)

(better late than never)

/Mike

---

### Post by v1nsai on 2010-01-14
This is an old thread, but I'm going to post here instead of starting a new one since it was never fully answered.

Thanks for the tip about devhelp-glibc-doc, that worked great.  I've been looking around for a similar package for libstdc++ and have found nothing.

I was looking around for how to package the libstdc++ into a devhelp readable format, but the closest I have found to anything relevant is [this]("http://old.nabble.com/devhelp-book-for-glibc-and-standard-C%2B%2B-libraries--td20407671.html").  In the first reply, the person suggests using a doxygen script to use with devhelp.

I haven't been able to figure out what this means yet, but maybe if someone else out there knows more we can get c++ working with devhelp.

---

### Post by buratinas on 2011-01-04
Hi,

Renewing old thread since the libstdc++ problem is apparently still unsolved.

The problem with straight doxygen -> devhelp approach is that standard library is quite tightly coupled with the language itself i.e. a lot of the time I look for an explanation of one or another language detail. Hence libstdc++ docs are not very suitable since at we'd need some additional documentation appended to the upstream one and these patches can quickly become a burden.

Some time ago I tried a solution of making a separate documentation by downloading an online manual and manually creating an devhelp book index. I tried this with cplusplus.com and was left satisfied. However there's a problem as I can't distribute (e.g. post here) the resulting *.deb because the material is copyrighted and very unlikely to be opensourced. Another problem is that we can't edit the material (e.g. in order to add c++0x features) since we don't have access underlying (wiki?) source.

So now I'm using the cplusplus.com book and improving  opensource wiki documentation at cppreference.com/wiki/start2 . Maybe some would be interested in improving that wiki so one day we have good standard library documentation?

I attach the devhelp book file of cplusplus.com. Search also works. I will compile full cppreference.com book and post here at some time later since currently I use cplusplus.com one and don't have enough time.

---

### Post by cjnucette on 2011-02-26
It would be nice if you can drop some instructions on how to install it on devhelp.

thanks.

---

### Post by ter31 on 2011-09-19
There has been some progress lately with regard to this problem. There's a c++ library reference at [<Cppreference.com>]("http://en.cppreference.com") wiki and now they provide an archived version as a Devhelp book [<here>]("http://en.cppreference.com/w/Cppreference:Archives"). Search also works!

---

