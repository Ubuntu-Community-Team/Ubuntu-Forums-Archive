---
title: "libstdC++ version"
date: 2008-10-18
forum: Programming Talk
---

### Post by jamesdcarroll on 2008-10-18
I need to install version 5 from the Debian packages to get Google's Web Toolkit to work, but the Package Manager warns that a newer version is available and suggests that I use that. And sure enough, I have version 6.

If I install version 5 as well am I gonna totally hose my system?

---

### Post by dwhitney67 on 2008-10-18
Have you determined whether or not Google's Web Toolkit will work with version 6?

---

### Post by jamesdcarroll on 2008-10-18
> **dwhitney67 said:**
> Have you determined whether or not Google's Web Toolkit will work with version 6?

Yes and no.

When I try to run the demo program in what's called "hosted" mode (which from what I gather 'fakes' a browser/server setup for debugging) is fails with:

** Unable to load Mozilla for hosted mode **
java.lang.UnsatisfiedLinkError: /home/jim/InstallStuff/gwt-linux-1.5.3/mozilla-1.7.12/libxpcom.so: libstdc++.so.5: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:770)
	at java.lang.System.load(System.java:1005)
	at com.google.gwt.dev.shell.moz.MozillaInstall.load(MozillaInstall.java:190)
	at com.google.gwt.dev.BootStrapPlatform.init(BootStrapPlatform.java:49)
	at com.google.gwt.dev.GWTShell.main(GWTShell.java:354)

There's doc/ other reports that this is an issue that they are aware of but aren't fixing yet because of all the other versions of linux out there that might not have the right version either.  I suspect that if I re compiled the whole lot against version 6 it would probably work, but I wouldn't know where to begin.

---

### Post by snova on 2008-10-18
Well, it definitely looks like you need libstdc++ version 5.

I think I actually have it installed on my machine (the only precompiled Linux binary I've every downloaded needed it), and I've never had a problem with it. It's just another version of a library- the rest of the C++ programs are linked against v6, so they won't collide.

Newly compiled C++ code links against v6, as I just confirmed.

So no problems.

---

### Post by jamesdcarroll on 2008-10-18
> **snova said:**
> Well, it definitely looks like you need libstdc++ version 5.

I think I actually have it installed on my machine (the only precompiled Linux binary I've every downloaded needed it), and I've never had a problem with it. It's just another version of a library- the rest of the C++ programs are linked against v6, so they won't collide.

Newly compiled C++ code links against v6, as I just confirmed.

So no problems.

I crossed my fingers and hit install and everything seems ok.

Thank you very much!

---

