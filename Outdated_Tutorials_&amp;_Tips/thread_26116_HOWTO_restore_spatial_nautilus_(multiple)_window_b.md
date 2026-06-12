---
title: "HOWTO: restore spatial nautilus (multiple) window behaviour"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by stoneguy on 2005-04-11
Someone suggested doing this from 
System Tools|Configuration Editor|Administration|apps|nautilus|preferences
but when I got there, the key was marked not writable in the tool.

I don't take NO for an answer. Change it directly as below.

sudo nano /root/.gconf/apps/nautilus/preferences/%gconf.xml
change the value to "false" on the line containing no_ubuntu_spatial
Save and exit nano

Do the same for ~/.gconf/apps/nautilus/preferences/%gconf.xml in each ID that was created.

---

