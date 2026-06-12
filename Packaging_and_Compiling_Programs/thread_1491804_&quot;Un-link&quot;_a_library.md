---
title: "&quot;Un-link&quot; a library"
date: 2010-05-24
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-05-24
Is there a way to un-link a library so that it is not considered a dependency?  For example, I am using wxWidgets which tells the compiler to link to libz.a.  But I am not using wxZip, so I do not need to link to libz.a.  

Would it be something like:
```
-ulibz
```?  (I know that doesn't work)

Or do I have to compile wxWidgets without zlib support?

---

### Post by snova on 2010-05-24
> **dodle said:**
> Is there a way to un-link a library so that it is not considered a dependency?  For example, I am using wxWidgets which tells the compiler to link to libz.a.  But I am not using wxZip, so I do not need to link to libz.a.

You aren't, but wxWidgets apparently is. You can't. Why would you want to?

> Or do I have to compile wxWidgets without zlib support?

If it's even possible. Consider also that wxWidgets itself might not even use zlib; perhaps one of its dependencies does. "ldd" output (if you're using this) doesn't just list the libraries you directly link to; it's every library that is eventually pulled into the running binary's address space.

---

### Post by dodle on 2010-05-24
Okay, so the only way to do it is to compile wxWidgets without zlib?  I can configure/make with the option "--without-zlib".

wxZip is the only part of wxWidgets that uses zlib.

---

### Post by snova on 2010-05-24
> **dodle said:**
> Okay, so the only way to do it is to compile wxWidgets without zlib?  I can configure/make with the option "--without-zlib".

Yes. It's silly though.

---

### Post by dodle on 2010-05-24
Okay, thank you snova.

**Edit:** I've actually decided to build wx with the option "--enable-zlib=builtin", so that when I cross-compile for Windows, I don't have to include libz.dll with my apps.

---

