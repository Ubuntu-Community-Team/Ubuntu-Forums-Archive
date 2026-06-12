---
title: "Collabcad installation"
date: 2020-07-06
forum: New to Ubuntu
---

### Post by kumarkv108 on 2020-07-06
Hi,
I do not know if this is the right forum to ask my question.

I want to install a software collabcad on Ubuntu 20.04. But getting below error.
Could advice me how to fix it.

LD_LIBRARY_PATH ./linux/lib:./linux/lib/other_libs:/usr/X11R6/lib
Exception in thread "main" java.lang.UnsatisfiedLinkError: exception occurred in JNI_OnLoad
	at java.lang.ClassLoader$NativeLibrary.load(Unknown Source)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.loadLibrary0(Unknown Source)
	at java.lang.System.<unknown>(Unknown Source)
	at sun.security.action.LoadLibraryAction.<unknown>(Unknown Source)
	at java.security.AccessController.<unknown>(Unknown Source)
	at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
	at sun.awt.DebugHelper.<clinit>(Unknown Source)
	at sun.awt.DebugHelper.create(Unknown Source)
	at java.awt.Component.<clinit>(Unknown Source)
	at incad.CollabCAD.main(CollabCAD.java:105)


Regards,

---

### Post by kumarkv108 on 2020-07-06
Dear All,

I see similar thread on this topic, but could not understand the fix.
Could guide me please

[https://ubuntuforums.org/showthread.php?t=1067313](https://ubuntuforums.org/showthread.php?t=1067313)

Regards,

---

### Post by dino99 on 2020-07-06
Linux install howto at [https://collabcad.gov.in/installationSteps.html](https://collabcad.gov.in/installationSteps.html) ( ~end of page)
but : may not work on new releases in 2019-20.

---

