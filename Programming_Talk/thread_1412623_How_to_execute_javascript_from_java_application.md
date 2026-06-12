---
title: "How to execute javascript from java application?"
date: 2010-02-21
forum: Programming Talk
---

### Post by Cig on 2010-02-21
Hi.
I need to call a javascript function from my java application.
That would be something like clicking a button in photoalbum to scan picture names. Now I use URLConnection and BufferedReader to parse html for picture titles.

Thank you.

---

### Post by Reiger on 2010-02-21
There's something called Live Connect. Alternatively you can make use of the browserjs engine (a wrapper around the Live Connect thing) the JSR 223 reference implementation provides. (Look for downloads files for JSR 223 on dev.java.net.)

---

### Post by Cig on 2010-02-21
Thank you for the help.

---

