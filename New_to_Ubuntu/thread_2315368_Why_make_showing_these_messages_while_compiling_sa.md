---
title: "Why make showing these messages while compiling sane-backends?"
date: 2016-02-28
forum: New to Ubuntu
---

### Post by pavlushka on 2016-02-28
I tried to compile the sane-backends from source but getting the following messages after running make, to configure, I ran ./configure --enable-avahi BACKENDS='canon genesys test'

make[1]: Leaving directory /home/.../sane-backends/po'
Making all in testsuite
make[1]: Entering directory/home/.../sane-backends/testsuite' Making all in sanei make[2]: Entering directory /home/.../sane-backends/testsuite/sanei'
run 'make check' to run tests
make[2]: Leaving directory/home/.../sane-backends/testsuite/sanei' Making all in tools make[2]: Entering directory /home/.../sane-backends/testsuite/tools'
Use 'make check' to run the tests.
run 'make check' to run tests
make[2]: Leaving directory/home/..../sane-backends/testsuite/tools' make[2]: Entering directory /home/.../sane-backends/testsuite'
make[2]: Nothing to be done for all-am'. make[2]: Leaving directory /home/..../sane-backends/testsuite'
Use 'make test' to run the tests.
make[1]: Leaving directory/home/.../sane-backends/testsuite' make[1]: Entering directory /home/.../sane-backends'
make[1]: Nothing to be done for all-am'. make[1]: Leaving directory `/home/.../sane-backends'

What's wrong with for all-am?:confused::confused::confused:

---

### Post by steeldriver on 2016-02-28
AFAIK that means there's nothing wrong with it - just that the target `all-am`is up-to-date

---

### Post by pavlushka on 2016-03-02
Okay, got it, Thanks

---

