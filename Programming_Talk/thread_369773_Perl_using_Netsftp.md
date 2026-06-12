---
title: "Perl using Net::sftp"
date: 2007-02-24
forum: Programming Talk
---

### Post by Gorf on 2007-02-24
I'm trying to write some automation scripts with Perl using the Net::SFTP module.  I have tried repeatedly to get it to install via CPAN but it always fails in the tests.  The other annoyance is the (what seems like) endless dependancies that I must answer "y" to to install.

Can this module be installed via apt-get or am I stuck installing it via CPAN?  And if so, can someone tell me what it is called in apt?

Cheers.

---

### Post by scoon on 2007-02-25
Hey there, 

Why not try and download the module and install it manually.  Maybe that will give you better errors than CPAN does.  All thought, I doubt that will make a difference, it is still worth a try.

-scoon

---

### Post by telebrett on 2007-06-18
You have to install the libgmp3-dev package. Math::GMP was not being made because "gmp.h" did not exist. You may also have to clean out the .cpan build directory for Math::GMP

---

