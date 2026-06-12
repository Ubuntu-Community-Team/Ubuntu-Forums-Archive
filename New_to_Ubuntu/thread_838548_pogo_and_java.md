---
title: "pogo and java"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by drascus on 2008-06-23
I update my computer from 7.10 to 8.04. now upon loading some pogo games in firefox I get an error that says "applet death" which appears in the status bar at the bottom of the window. Does anyone know what this is or how it could be fixed? thanks...

---

### Post by ZabiGG on 2008-06-27
If you're using the 64-bit version of firefox, java applets and java webstart are not yet supported (source: sun java installation site). 

I tried to install the 32-bit version to solve this issue ([http://ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+firefox](http://ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+firefox)), but a dependency file is no longer in the repositories, so it does not work. 

For now, as a workaround, I'm using the iced tea java plugin since the sun-java6-plugin is no longer in the repositories either. It works for some pogo games, but not all.

Sorry I couldn't be more help.

Z.

---

### Post by S1xp4ck on 2008-06-27
I have had multiple issues with both Pogo and Yahoo.  It seems Java 1.6 just refuses to work right. Once I reverted to Java 1.5 everything was good in pogo world.

---

