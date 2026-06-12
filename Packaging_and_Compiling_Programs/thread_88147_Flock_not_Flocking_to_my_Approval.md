---
title: "Flock not Flocking to my Approval"
date: 2005-11-09
forum: Packaging and Compiling Programs
---

### Post by kvidell on 2005-11-09
> +++ making chrome /home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock/tabs  => ../../../../dist/bin/chrome/browser.jar
+++ overriding content/browser/flock/tabs/tabsOverlay.xul content/browser/flock/tabs/tabsOverlay.css content/browser/flock/tabs/tabs.xml content/browser/flock/tabs/close.png content/browser/flock/tabs/close_active.png content/browser/flock/tabs/close_inactive.png content/browser/flock/tabs/close_hover.png 
updating: content/browser/flock/tabs/tabsOverlay.xul (stored 0%)
updating: content/browser/flock/tabs/tabsOverlay.css (stored 0%)
updating: content/browser/flock/tabs/tabs.xml (stored 0%)
updating: content/browser/flock/tabs/close.png (stored 0%)
updating: content/browser/flock/tabs/close_active.png (stored 0%)
updating: content/browser/flock/tabs/close_inactive.png (stored 0%)
updating: content/browser/flock/tabs/close_hover.png (stored 0%)
make[5]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock/tabs'
make[5]: Entering directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock/lucene'
make[6]: Entering directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock/lucene/src'
make[6]: *** No rule to make target `../../../../../../local/lib/libclucene.a', needed by `libxpcomclucene.so'.  Stop.
make[6]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock/lucene/src'
make[5]: *** [libs] Error 2
make[5]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock/lucene'
make[4]: *** [libs] Error 2
make[4]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components/flock'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser/components'
make[2]: *** [libs] Error 2
make[2]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla/browser'
make[1]: *** [tier_99] Error 2
make[1]: Leaving directory `/home/kvidell/source/flock-source-0.4.10-complete/mozilla'
make: *** [default] Error 2Any ideas? :-\ I don't understand the output.

Anything else I should paste to help?
- Kev

---

### Post by edwardog on 2005-11-09
Looks like a problem in the Makefile for Lucene.

I'll take a look when this finishes compiling.

---

### Post by flickerfly on 2006-06-15
Since this post, flock has moved from 0.4 to 0.7. Has anyone tried the updated version? Is there a package for it somewhere?

---

### Post by edwardog on 2006-06-15
I've taken Flock 0.7 for test drive and it's working out really well.

---

