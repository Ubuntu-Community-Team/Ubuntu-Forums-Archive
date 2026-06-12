---
title: "Eclipse: set default to Sun java jdk 5"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by andrew222 on 2008-11-09
Does anyone know how to switch the default Java compiler in Eclipse from gcj to the sun java compiler?

---

### Post by bettlebrox on 2008-11-09
Go to Window->Preferences->Java->Installed Runtimes to add alternative JVM's.

If you want to change the version of Java that Eclipse actually runs on you need to have a different JVM on your PATH. The easiest way to do this is to run galternatives and change the default version of Java used on your system.

---

### Post by andrew222 on 2008-11-10
What path would I use to choose the sun java jvm?

---

### Post by bettlebrox on 2008-11-10
To where ever it's installed. :) Did you install Sun's 1.5 JDK?

---

### Post by andrew222 on 2008-11-10
Yes, I did install jdk 1.5. Net Beans uses it but I can't seem to find a way to make it work for Eclipse.

---

### Post by __Frank__ on 2008-11-11
follow the above steps and browse to:

/usr/lib/jvm/java-5-sun

Cheers,
Frank

---

### Post by andrew222 on 2008-11-11
Thank you very much.

Have a pleasant day.

---

