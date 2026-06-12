---
title: "Ant's using a different java version than Eclipse"
date: 2008-06-16
forum: Programming Talk
---

### Post by Winterhart on 2008-06-16
And unfortunately, it's using the wrong version. >_>

My /usr/bin/java symlink goes to the right version: 1.5.0_10.  Eclipse is started with the -vm switch which directs it to the right version (I think).  Ant, however, is still compiling with 1.6.0.06!

Screenshot:
[IMG]http://i16.photobucket.com/albums/b15/_winter_icons_/misc/Screenshot-1.png[/IMG]

Does anyone know how to make ant *listen* to Eclipse?

---

### Post by ysse on 2008-06-25
For me, Ant uses the JRE that is checked in Windows/Preferences, Java - Installed JREs.

But I had to add Sun 1.5.0 manually, using the path /usr/lib/jvm/java-1.5.0-sun/jre

---

