---
title: "[SOLVED] frostwire not loading after upgrade to 8.04"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Indy452 on 2008-05-15
After I upgraded to 8.04 a couple of weeks ago I am unable to open frostwire program anymore. Its still listed in my apps>internet tab but when I click it I can hear the processor work for a second but nothing comes up. What can I do to repair this issue?

I don't use frostwire much but I do like the programs I have installed to work properly.

Thank you.

Neal

---

### Post by hermes0710 on 2008-05-16
Try running frostwire through a terminal to see the error

---

### Post by quibbler on 2008-05-16
check your java...frostwire needs version 1.5 or higher

Regards quibbler

---

### Post by hermes0710 on 2008-05-16
Ignore this post (sorry) :)

---

### Post by Indy452 on 2008-05-16
> **quibbler said:**
> check your java...frostwire needs version 1.5 or higher

Regards quibbler

Hi, sorry I'm so late getting back with ya.

I have java but not sure which version. How do I tell which version of java I have?  It worked fine before the upgrade from 7.10 to 8.04 any clues?

Neal

---

### Post by quibbler on 2008-05-16
open synaptic package manager and search for sun-java
either sun-java5 or sun-java6 has to be installed

Regards quibbler

---

### Post by HotShotDJ on 2008-05-16
The likely culprit is openjdk -- even if you have sun-java5 or sun-java6 installed.  Open Synaptic Package Manager and search for openjdk.  Any openjdk packages that are installed, mark for _complete_ removal.  Also any icedtea packages.  Now, apply.

Now, search for sun-java -- you want either version 5 or 6.  If not installed, pick either sun-java5-plugin or sun-java6-plugin and mark for installation... this will pull in the rest of java and install the plugin for Firefox.

If the sun-java packages that you want are already installed, mark all the relevant packages for reinstallation.

After all this is done, log out and back in (no need to reboot).  Fire up Frostwire.

---

### Post by Indy452 on 2008-05-19
> **HotShotDJ said:**
> The likely culprit is openjdk -- even if you have sun-java5 or sun-java6 installed.  Open Synaptic Package Manager and search for openjdk.  Any openjdk packages that are installed, mark for _complete_ removal.  Also any icedtea packages.  Now, apply.

Now, search for sun-java -- you want either version 5 or 6.  If not installed, pick either sun-java5-plugin or sun-java6-plugin and mark for installation... this will pull in the rest of java and install the plugin for Firefox.

If the sun-java packages that you want are already installed, mark all the relevant packages for reinstallation.

After all this is done, log out and back in (no need to reboot).  Fire up Frostwire.


Hey Thanks!! I followed your directions to the "T" and it is working again (yeah).

Sorry I'm getting back so late with ya.

Neal

---

