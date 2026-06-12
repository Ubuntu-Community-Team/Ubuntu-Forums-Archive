---
title: "APT + .debs vs. Perl CPAN + Python easy_install + Ruby Gems + PHP PEAR"
date: 2007-06-17
forum: Packaging and Compiling Programs
---

### Post by eddymul on 2007-06-17
I noticed that Ubuntu packaged some Perl CPAN stuff as lib-*-perl.

I noticed that Ubuntu packaged some Python Cheese Shop stuff as python-*.

I noticed that Ubuntu packaged some R CRAN stuff as r-cran-*.

What is Ubuntu's policy toward CPAN/Cheese-Shop/CRAN packages (and Ruby Gems and PHP PEAR/PECL)?

Do we package them as .deb packages?

Or do we tell users to use CPAN/easy_install/install.packages()?

---

### Post by leibowitz on 2007-06-27
You should ask this on some mailing-list related to packaging rules. 

I really don't know the answer.

---

### Post by KaeseEs on 2007-06-28
Some commonly installed modules for Perl, Python, Ruby etc. have their own packages.  This is to ease quick customization of a system.  I know that, at least in the case of Perl, CPAN works perfectly and doesn't conflict with anything.

---

### Post by eddymul on 2007-07-01
> **KaeseEs said:**
> I know that, at least in the case of Perl, CPAN works perfectly and doesn't conflict with anything.

In the case of Python, setuptool's easy_install works perfectly, too.

---

