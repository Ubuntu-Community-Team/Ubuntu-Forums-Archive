---
title: "GTK SWT x86 or x86_64?"
date: 2011-07-15
forum: Programming Talk
---

### Post by stchman on 2011-07-15
Hello all.

I am interested in the SWT for GTK.  I see there is a6 x86 and an x86_64.  Is there really a need for a 64 or 32 bit JAR file.  I mean they are just Java commands.

Can someone elaborate?

Thanks.

---

### Post by t1497f35 on 2011-07-15
A .jar file is just a .jar file.
If it's cross-platform or bit resolution independent depends on what's inside it and on the logic of the source code (what the .class files are doing).
In your case, if you unzip the .jar file you'll find .so libraries which are 32 or 64 bit.

---

