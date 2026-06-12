---
title: "[SOLVED] gcc-3.3-doc &amp;amp; gcc-3.4-doc what is the fix?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by harryliddic on 2008-07-29
what is the fix for the gcc-3.3-doc and gcc-3.4-doc errors?

---

### Post by LinuxRocks713 on 2008-07-31
> **harryliddic said:**
> what is the fix for the gcc-3.3-doc and gcc-3.4-doc errors?

I have no idea what you are talking about, but try one of the following:

```

sudo dpkg --remove --force --purge gcc-3.3-doc #to remove gcc3.3 doc and keep gcc 3.4
sudo dpkg --remove --force --purge gcc-3.4-doc #to remove gcc3.4 doc and keep gcc3.3doc

```

---

### Post by harryliddic on 2008-08-09
the solution I have found is counter-intuitive. Eliminate both gcc3.3 and gcc3.4 along with the docs and dpkg has nothing to look for.

---

