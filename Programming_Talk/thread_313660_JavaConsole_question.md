---
title: "JavaConsole question"
date: 2006-12-06
forum: Programming Talk
---

### Post by huggy77 on 2006-12-06
This is probably a stupid question - but here goes...

how do i open the javaConsole?  I am writing some servlet code that outputs to the console - but i cannot open the console becuase i am NOOB.

Thanks in advance!

java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)

---

### Post by Keffin on 2006-12-06
How are you running the servlet? If it is in tomcat then you'll find it in tomcats log file (catalina*.out), I assume it would be a similar arrangement with other systems.

---

### Post by DaveBorealis on 2006-12-06
> **huggy77 said:**
> i cannot open the console

Hello,

If you're using Gnome, go to 'System->Preferences->Sun Java 5.0 Plugin Control Panel' and click the 'Advanced' tab and the 'Java console' selector.  There's a radio button to unhide it.  (However I haven't used it yet myself, so I don't know where it appears when it isn't hidden.  I just ran a java app to see for myself, and darn if I can find it!)

Maybe this'll get you closer to finding it.

Dave

---

### Post by huggy77 on 2006-12-07
i am using kde...  never thought about searching for kde java instead of ubuntu java - because i am THICK

---

### Post by huggy77 on 2006-12-08
still no joy -

---

### Post by DaveBorealis on 2006-12-08
> **huggy77 said:**
> still no joy -

Have you tried the cli command 'jconsole'?  Don't know if that's what you want or if it's in your distribution.  Here's how I found it:
```
$ locate java | grep console
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/man/man1/jconsole.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/man/ja/man1/jconsole.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/jconsole
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/lib/jconsole.jar

```

Dave

---

