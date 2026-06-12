---
title: "What is gtkhelper?  Why does it freeze my Java apps?"
date: 2008-02-14
forum: Programming Talk
---

### Post by skullmunky on 2008-02-14
(This might be better filed under Desktop Environments, but I wasn't sure. )

I'm using Processing ([www.processing.org](www.processing.org)), version 0135.  Here's the problem: bringing up dialog boxes (for example, "Save As..."), causes the app to apparently freeze.  Another process gets spawned, something called "gtkhelper".  Killing it returns everything to normal.  I saw a bug posted with precisely this behavior with java/Swing apps in general, but it's expired.  

I'm using 7.04 and KDE.  Processing comes with its own JRE, so I * think * this makes it independent of the version of Java I have configured systemwide.  Here's what java -version tells me:

```

java version "1.5.0_12"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_12-b04)
Java HotSpot(TM) Server VM (build 1.5.0_12-b04, mixed mode)

```

I have some older versions of Processing that don't have this bug, which use JRE 1.4.2.  OTOH using 1.5 seems to make everything else way faster and better :) 

I'm not sure where to start tackling this, other than trying different JRE's, so any suggestions would be great...

---

