---
title: "perl cpan make install NOT OK"
date: 2008-02-10
forum: Packaging and Compiling Programs
---

### Post by ruy_lopez on 2008-02-10
I'm just posting this for the record. I've spent the last few hours fighting with perl cpan. 

It was building modules fine, they were testing without error, but none of them would install.

I was getting an error like this:
/usr/bin/make install NOT OKAY

There are a few dead old threads with the same problem. However, none of them offer much of a solution. Eventually I tracked it down to PDFlibLite. When I installed PDFLibLite, it actually created a file in the perl module install path. Perl modules install into /usr/local/lib/perl/5.8.8. PDFLibLight actually created a file *called* "5.8.8" *inside* "/usr/local/lib/perl". Completely Nuts.

Hopefully the next time someone gets this error, when they google they'll get this thread, and check nothing is blocking the install path.

I know, I get what I deserve for installing a commercial library.

---

### Post by nseger on 2008-02-18
I experienced the same problem on Ubuntu Server 7.10.

I tried to install Bundle::CPAN and got a large number of failed makes.

By entering all the folders under .cpan/build and running a manual

perl Makefile.pl
make
make install

I manged to get all the parts of Bundle::CPAN installed and CPAN upgraded. After this it seems to work as it should installing additional modules.

/N

---

### Post by tayl0r on 2008-03-19
I had this same problem but my solution was to install these Ubuntu packages via apt-get:

build-essential autoconf automake libtool gdb

You probably also need some other ones like gcc, etc. Unfortunately I don't have the exact list. Hopefully every ubuntu package is either listed above or is a requirement of those packages.

I was running a new minimal ubuntu install via vmware on my XP box so I had almost no packages installed by default.

---

### Post by mobin on 2011-10-13
> **tayl0r said:**
> I had this same problem but my solution was to install these Ubuntu packages via apt-get:

build-essential autoconf automake libtool gdb

You probably also need some other ones like gcc, etc. Unfortunately I don't have the exact list. Hopefully every ubuntu package is either listed above or is a requirement of those packages.

I was running a new minimal ubuntu install via vmware on my XP box so I had almost no packages installed by default.
After wasting so much time fighting with Perl module dependency issues while trying to install Bugzilla, this finally got everything building for me.

---

