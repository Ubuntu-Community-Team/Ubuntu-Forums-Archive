---
title: "Trouble updating Eclipse"
date: 2007-10-06
forum: Programming Talk
---

### Post by japtar10101 on 2007-10-06
Well, I'm having trouble updating the pydev plugin for Eclipse because apparently, it can't make any directories or files.
As such, this is the error code:
```
Unable to complete action for feature "PyDev for Eclipse" due to errors.
  Unable to create file "/usr/lib/eclipse/plugins/org.python.pydev.core_1.3.9/META-INF/MANIFEST1191686297019.MF". [/usr/lib/eclipse/plugins/org.python.pydev.core_1.3.9/META-INF/MANIFEST1191686297019.MF (No such file or directory)]
  Unable to create file "/usr/lib/eclipse/plugins/org.python.pydev.core_1.3.9/META-INF/MANIFEST1191686297019.MF". [/usr/lib/eclipse/plugins/org.python.pydev.core_1.3.9/META-INF/MANIFEST1191686297019.MF (No such file or directory)]

```
It seems that all other plugins I'm trying to install (including a new version of Eclipse:-o!) cannot install without pydev first.  What's up with all the "permission denied"?  Should I make the Eclipse directory public or something?

---

### Post by kalos on 2008-02-18
The apt-get install of Eclipse uses /usr/lib/eclipse and this is owned by root. If you run eclipse using:
 ```
sudo eclipse
```
and install your plugins, then I think it should work.
**But**, you should **only** run Eclipse like this when you are installing/updating plugins (it's not a good idea to do regular development like this).


Or you could probably run
 ```
sudo chown -R YOURUSERID /usr/lib/eclipse
```
or something like that, but I'm not sure if that's a good idea. Anyone else have ideas?

I ended up just downloading the tarball and unpacking it into *~/bin/eclipse*. This is easier (and I can get the 3.3 version that I need), but it's disappointing that I didn't get to use the apt-get version of eclipse and eclipse-pydev.

-kalos

---

### Post by kimberlite on 2009-04-15
It can be useful to launch eclipse from terminal to see error messages. There was a missing folder at my install /usr/local/lib/eclipse/.eclipseextension. After I have created and owned as prompted by eclipse, and followed kalos useful suggestions in previous post, it was possible to install PyDev plugin.

---

