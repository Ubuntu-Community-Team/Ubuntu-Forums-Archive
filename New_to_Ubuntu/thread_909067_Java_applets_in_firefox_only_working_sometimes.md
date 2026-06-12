---
title: "Java applets in firefox only working sometimes"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by rrcs on 2008-09-03
I'm having trouble with Java applets in Firefox 3.0.1. Sometimes they'll work fine, but more often what happens is:

While a page loads, I may be able to see the Java object (like the clocks on the [w3 Java test page]("http://www.w3.org/People/mimasa/test/object/java/clock")), but as it finishes loading, all I get is grey squares (cf. attached screenshot).

According to Synaptic, I have the following sun-java6 packages installed:

sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin

Firefox Add-ons tell me I have the "Java(TM) Plug-in 1.6.0_06-b02" installed.

Any idea why I'm sometimes getting grey squares?

---

### Post by alienexplorers on 2008-09-07
Try adding a symbolic link to firefox-addons in the /usr/lib directory.
Go to the /usr/lib/firefox-addons/plugins.
The link should look something like this:
> ln -s /usr/lib/jvm/java-6-sun-*/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

---

### Post by rrcs on 2008-11-04
Hi.

Thank you for replying - I've been waiting for the issue to arise again to try your fix, but for some reason Java/Firefox has been playing nice ever since. I will keep it in hand to try, though, should it start acting up again.

---

