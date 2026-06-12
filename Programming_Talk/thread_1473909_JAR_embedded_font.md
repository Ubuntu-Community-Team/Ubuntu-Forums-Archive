---
title: "JAR embedded font"
date: 2010-05-05
forum: Programming Talk
---

### Post by .:PiXi²:. on 2010-05-05
Hi, is it possible to embed a font in a JAR-package?
Because I have a small program that uses a custom font, but I want to be sure that the text displays correctly on other computers as well.

Thanks in advance!

---

### Post by Reiger on 2010-05-05
Yes, through a combination of Font.createFont() and ClassLoader.getResourceAsStream().

---

### Post by .:PiXi²:. on 2010-05-07
Got it working, thanks Reiger.

---

