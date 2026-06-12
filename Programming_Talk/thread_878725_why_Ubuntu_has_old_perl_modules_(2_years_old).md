---
title: "why Ubuntu has old perl modules (2 years old) ?"
date: 2008-08-03
forum: Programming Talk
---

### Post by bs0d on 2008-08-03
Yesterday I noticed that many of perl modules are very old. 

I am developing perl script and it produce strange warnings in Encode module, but the same script works silent on other machine. After investigating I found the roots of the problem: my Encode.pm was very old, version 2.12. Updated with CPAN to 2.26 and the warnings was gone.

So my question is why the old modules included: because of security or other reason?

Thanks

---

