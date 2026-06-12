---
title: "Limewire/Frostwire Issues in Intrepid (Help the noob :p)"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by rfsquared on 2008-11-06
Hey guys and gals,

I recently made the switch completely over to Linux...I upgraded my OS and now I'm running Intrepid Kubuntu.  Anyway, I've always done music on my Windows partition before but now I obviously need to do it on Linux.

I'm having some issues.

Firstly, Limewire's Debian package needs to install 2 Java packages to work, neither of which will install.  I get those stupid errors that say like "Report Problem" or whatever.

So that didn't work.  So then I tried installing Frostwire.  The package installed correctly but then when I go to my Apps menu and click the program, the little icon bounces for ten seconds, Frostwire appears briefly on the taskbar and then goes away.

WTF do I do?

---

### Post by gn2 on 2008-11-06
When I had that problem (but on Ubuntu 8.04) the cure was to remove the openjdk packages with Synaptic and install the java-common package.

---

### Post by rfsquared on 2008-11-06
Thanks so much!  Worked perfectly on Intrepid, except instead of Java-Common I just went on Adept and installed the Sun JRE 6 release (make sure it's the one with DEPENDENT architecture...the independent option doesn't work for me)

---

### Post by shanix on 2008-11-11
Just so everyone knows, the actual package is called:

openjdk-6-jre

---

