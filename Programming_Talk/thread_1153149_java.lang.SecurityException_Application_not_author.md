---
title: "java.lang.SecurityException: Application not authorized to access the restricted API"
date: 2009-05-08
forum: Programming Talk
---

### Post by pedroezsa on 2009-05-08
```
java.lang.SecurityException: Application not authorized to access the restricted API
        at com.sun.midp.security.SecurityToken.checkIfPermissionAllowed(SecurityToken.java:170)
        at com.sun.midp.security.SecurityToken.checkIfPermissionAllowed(SecurityToken.java:145)
        at com.sun.midp.midletsuite.MIDletSuiteImpl.checkIfPermissionAllowed(+8)
        at com.sun.midp.midlet.MIDletState.<init>(+83)
        at javax.microedition.midlet.MIDletProxy.<init>(MIDletProxy.java:33)
        at javax.microedition.midlet.MIDlet.<init>(MIDlet.java:70)
        at SendMailForMe.<init>(SendMailForMe.java:46)
        at SendMailForMe.commandAction(SendMailForMe.java:236)
        at javax.microedition.lcdui.Display$DisplayAccessor.commandAction(+282)
        at javax.microedition.lcdui.Display$DisplayManagerImpl.commandAction(+10)
        at com.sun.midp.lcdui.DefaultEventHandler.commandEvent(+68)
        at com.sun.midp.lcdui.AutomatedEventHandler.commandEvent(AutomatedEventHandler.java:670)
        at com.sun.midp.lcdui.DefaultEventHandler$QueuedEventHandler.handleVmEvent(+186)
        at com.sun.midp.lcdui.DefaultEventHandler$QueuedEventHandler.run(+57)
```

I was confused whether here is the right place to ask or not :) but i think the error has something to do with permission. And i don't have any idea how to fix it. I'm using hardy and trying to run a program for mobile via emulator  :confused:

---

### Post by Reiger on 2009-05-08
Java has a few built-in Security "principials" which are used to control (and limit privileges of) applets inside the browser plugin for instance. They work via a negotiation mechanism: each "running instance" has a classloader with a security manager. Whenever something for which security "policies" have been defined is accessed by the "running instance" (applet, application, w/ever), there is a lookup performed via the Security Manager to check if the app is allowed access.

... Which is where it failed in your case.

But how does the Security Manager know? By default there are only 2 or 3 security profiles:
(a) Applet
(b) Application
(c) Signed versions (usually) with bumped privileges of above. Usually (b) runs as (c) even if it is not signed, but this is *not* the case if it is loaded via some other Java mechanism (custom class loaders) that inherit/use custom (more restrictive) Security Managers.

So the solution is fairly straightforward (albeit it will require some work/research on your part): you must sign your application and install your "signature". (And if neccesary create a security profile for your app.) 

SUN has a bunch of tutorials which deal with this, I suggest you read those instead of going by my -undoubtedly distorted by memory deficiencies- version of their words.

---

### Post by pedroezsa on 2009-05-18
Reiger, sorry for the long reply, it took me a long time to get my internet connection :D
I'm using MAIL4ME and i've signed my application to trusted (there is no maximum), but still doesn't work :( :(
should i get my signature from NetBeans or how??

---

