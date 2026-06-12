---
title: "How to set JVM Args? FF Icedtea"
date: 2011-03-22
forum: Programming Talk
---

### Post by owenlindsell on 2011-03-22
Anyone any idea where I set the JVM args for the ff java plugin?
I am using OpenJDK and IcedTea.

Cheers,
Owen

---

### Post by owenlindsell on 2011-03-22
Scatch that, I've moved over to Sun JDK and the Sun plugin now, but still have the same problem.

I set the VM args in ~/.java/deployment/deployment.properties.
These even show up in System->Preferences->Sun Java 6 Plugin Control Panel

However, when I start an applet in firefox and then check the JVM args using jconsole, I see they've been set to:
-D__jvm_launched=1283460253 -Xbootclasspath/a:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/deploy.jar/:/usr/lib/jvm/java-6-sun...

Any idea how to add to or override these?

Thanks in advance for any thought you may give this!

Owen

---

### Post by owenlindsell on 2011-03-22
This has somehow started working for me now. The JVM started picking up the settings after a reboot.

Thanks,
Owen

---

