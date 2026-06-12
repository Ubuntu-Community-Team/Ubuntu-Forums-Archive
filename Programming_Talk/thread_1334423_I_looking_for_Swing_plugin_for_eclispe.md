---
title: "I looking for Swing plugin for eclispe"
date: 2009-11-22
forum: Programming Talk
---

### Post by hoboy on 2009-11-22
I am looking for a swing plugin for eclipse-jee-galileo-SR1-win32
for gui programming

---

### Post by myrtle1908 on 2009-11-22
There are a few but I have had no success with any of them (the free ones).  They either don't work at all or don't do what I want.  So much so that I always end up hand coding UIs.

I recently tried *visualswing4eclipse* with galileo and ganymede.  Rubbish.

[http://code.google.com/p/visualswing4eclipse/](http://code.google.com/p/visualswing4eclipse/)

There is also the *Visual Editor Project* but like *visualswing4eclipse* it is also rubbish.  Neither have had new a release for some years and the docco is almost non existent.

[http://www.eclipse.org/vep/WebContent/main.php](http://www.eclipse.org/vep/WebContent/main.php)

I'm told there are some good ones that you can purchase but I have no experience with these.

You could try NetBeans whose GUI editor is much better than the Eclipse offerings.  I tried it last week but struggled with it.  It tries to be too helpful with "snapping" widgets etc. and I end up yelling at the damn thing.

If you must use a visual designer then definitely go for NetBeans but really, doing it by hand is the only way for Java UIs.

I would be interested if anyone else has had similar experiences.  I would love to find a UI designer for Java apps that are as good as the MS ones.  VB6 for all its language deficiencies had awesome UI tools.

---

### Post by Reiger on 2009-11-22
@Myrtle: heh, too true. 

If you want a GUI editor of sorts and you don't want to pay money for it you want Netbeans. However the damn thing isn't actually all that _easy_ to work with. Some pretty basic manipulations (e.g. swap two components vertically but keep their horizontal positions) or make sure that two given combo-boxes fix to the same size if they are *not* part of the same container... 

And that is what is to be considered well within the scope of GUI design. But the picture becomes quite a bit worse when more complex scenario's arise; such as e.g. custom resource loading.

---

