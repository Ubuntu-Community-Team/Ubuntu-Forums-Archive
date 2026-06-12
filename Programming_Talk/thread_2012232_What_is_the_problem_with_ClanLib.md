---
title: "What is the problem with ClanLib?"
date: 2012-06-28
forum: Programming Talk
---

### Post by youknowme on 2012-06-28
The Ubuntu repository has an obsolete version of ClanLib. So I decided to install it myself from source. After several hours of head banging I still never managed to get an 'example' class to compile. Even worse, I tried to build the html documentation after compiling the library and that failed with an error concerning a missing file.

It is sad because I know that the functions of this library are really easy to understand and use. Why don't the Ubuntu people fix this so we have a updated working automated install system for Clanlib??

In the end I decided to use SFML - and here is the kicker - it was bang up to date. Installed without a hitch and there is even a guide for setting it up with my particular IDE.

What the devil is going on with ClanLib? Does anyone know?

---

### Post by MadCow108 on 2012-06-29
the package seems orphaned or at least being neglected by its maintainer in debian. It had its last non qa type upload in 2009.
There is no dedicated ubuntu maintainer.
you might want to ping the debian games team about it, and maybe step up and help the maintainer or adopt it.
see [http://packages.qa.debian.org/c/clanlib.html](http://packages.qa.debian.org/c/clanlib.html) for all the relevant information and email addresses.

---

