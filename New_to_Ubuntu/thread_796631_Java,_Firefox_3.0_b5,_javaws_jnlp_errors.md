---
title: "Java, Firefox 3.0 b5, javaws jnlp errors"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by kukuku on 2008-05-16
The preinstalled FF3b5 in Ubuntu 8.04 has a problem running .jnlp files with Java Webstart. This is a bug that has been reported several times from what I deduced from the Google matches to it. I worked around this by downloading Java 1.6.0_05 from Sun and using the javaws executable from that archive. Now when I try to run jnlp files using it, it just gives the following error:

Bad installation. Error invoking Java VM (execv): No such file or directory

Is there any way to get javaws working in Ubuntu 8.04?

---

### Post by alienexplorers on 2008-05-29
I don't know if this would help, but the java package I loaded wass:
> sudo aptitude update
sudo aptitude -install sun-java5*

---

