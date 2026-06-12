---
title: "Checking package installation"
date: 2008-06-03
forum: Programming Talk
---

### Post by raevin on 2008-06-03
Simple question...is it programmically possible to see if a certain package that is installed, and if so, have any pointers or something?  Reason being is I want to write an automatic PHP install program, and I want it to check to see if the package needed for a certain feature (like libxml2 for xml support) is installed or not.

---

### Post by Vadi on 2008-06-04
I think "apt-cache showpkg" will help you. It says "W: Unable to locate package <name>" if it can't find one.

---

### Post by raevin on 2008-06-04
> **Vadi said:**
> I think "apt-cache showpkg" will help you. It says "W: Unable to locate package <name>" if it can't find one.

Thanks.! :D  Seems to be rather what I'm looking for.  I'll work with that and see what I can come up with.

---

