---
title: "different distribution requires different rules"
date: 2015-03-08
forum: Packaging and Compiling Programs
---

### Post by patrick75 on 2015-03-08
I'm packaging a program which makes use of the GNU Guile.

In trusty, it can normally be built using debhelper with autoreconf.

However, in precise, it cannot be built.

Due to the different version of autoconf(2.68-1 vs. 2.69-6), it generates different configure script.
As a result, in precise, it lacks of setting the variable "GUILD" and still uses that variable.

For correcting this, I "export GUILD=$(shell which guild)" in the debian/rules for precise.

And this solution make it inconsistent with the debian/rules in trusty.

Do I have a way to make it consistent?
I know there's at least 2 ways:
1. "export GUILD=$(shell which guild)" for trusty, too
2. using some if-else logic for testing the distribution, and set/no-set that variable
Is there any other elegant way to do this?



Another minor question, each time I upload the source package to my ppa, I need to change the distribution in debian/changelog.
Is there any way to automate this process or eliminate this step?
Solution: [http://askubuntu.com/questions/30145/ppa-packaging-having-versions-of-packages-for-multiple-distros](http://askubuntu.com/questions/30145/ppa-packaging-having-versions-of-packages-for-multiple-distros)

---

