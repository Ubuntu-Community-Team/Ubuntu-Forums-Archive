---
title: "Apache2 and Spanish character"
date: 2005-10-29
forum: Programming Talk
---

### Post by p1r0 on 2005-10-29
Hi all
I'm running apache2 and php4 on my Ubuntu 5.04 and Ican't get apache tu display my spanish charcater right. 
For example instead of ó or é it displays '?'.......:confused: 
I can't find a work around for this.

If anyone could help me I'd be most grateful.

p1r0.-

---

### Post by toojays on 2005-10-29
Does your HTML set the charset? For instance, this forum has "<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />" in the HTML header.

---

### Post by p1r0 on 2005-10-29
Yes that solved it.
I can't believe I forgot that. I guessed that my Apache2 on Windows has the charset set as default.

Thank you very much.

p1r0 - ;)

---

