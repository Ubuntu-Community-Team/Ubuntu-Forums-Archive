---
title: "Can't start program"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Will Walshe on 2008-05-02
I've installed the program **iriverter**, but can't get it to run.

Starting it up in a terminal window returns the error message:

!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! no swt-pi-gtk-3236 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1698)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:840)
!!! java.lang.System.loadLibrary(System.java:1047)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
	at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)


...which means very little to me. Anyone know what I have to do?

---

### Post by nowshining on 2008-05-03
go to my website and in the tips, tricks section try the fix for a similiar error for frostwire, my site url is in my sig, Ubuntu/Kubuntu Gatherings.

---

