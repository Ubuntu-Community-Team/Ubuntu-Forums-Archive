---
title: "SVN (or similar) Service With Write Access Via https"
date: 2006-07-13
forum: Programming Talk
---

### Post by knipknap on 2006-07-13
Can anyone name an online service that provides SVN (or any other RCS) write access for members via https? I would like to be able to access the repository from behind a proxy for which I do not have admin rights.

---

### Post by thumper on 2006-07-13
what about sourceforge or tigris.org?

---

### Post by knipknap on 2006-07-13
> **thumper said:**
> what about sourceforge or tigris.org?

Uuuhh. Ok, I did not know Sourceforge supports this configuration. However, it seems this means my proxy has to support the

PROPFIND, REPORT, MERGE, MKACTIVITY, CHECKOUT

methods for this to work. ([http://subversion.tigris.org/faq.html#proxy](http://subversion.tigris.org/faq.html#proxy))
Mine does not.

Any other options than SVN in this case? Of course, CVS won't work.

---

