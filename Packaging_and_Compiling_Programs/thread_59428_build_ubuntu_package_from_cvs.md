---
title: "build ubuntu package from cvs?"
date: 2005-08-23
forum: Packaging and Compiling Programs
---

### Post by chiefofthejojos on 2005-08-23
Hi, I want to make an ubuntu package for moto4lin (moto4lin.sf.net) but the author hasn't made a new release for over 6 months and there is a lot of core functionality that has been added since then.  Is it ok to build an ubuntu package from the cvs?  The latest release is "0.1-rc1".  Perhaps it is to immature of a project to be adding to the universe anyway.

---

### Post by strikeforce on 2005-08-24
You would have to ask the MOTU however I would think it was currently imature however I don't decide anything.  You might want to build it for yourself test it out awhile help the developer improve the product.

---

### Post by chiefofthejojos on 2005-08-26
I will build it for myself and test it out, but the developer hasn't answered my email.  :neutral:

---

### Post by ssmaxss on 2006-08-17
You could use deb from debian testing (install it using --force-depends). It works ok.

---

### Post by mlind on 2006-08-17
Or get sources from debian and compile it for your distribution. If you need cvs build, you can try using existing packaging information and build a cvs snapshot.

---

