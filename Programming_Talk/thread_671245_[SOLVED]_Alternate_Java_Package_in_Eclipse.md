---
title: "[SOLVED] Alternate Java Package in Eclipse"
date: 2008-01-18
forum: Programming Talk
---

### Post by sagarhshah on 2008-01-18
Hi.

Is there a way to install multiple versions of Java?

One of the modules I have at uni requires me to be using version 1.5.0_12 or something near that.

I asked my lecturere but unfortunately he doesn't know how t do it in linux.

Also how would I point Eclipse to the alternative version.

Any help would be appreciated.

Thanks

Sagar

---

### Post by kevykev on 2008-01-18
Hi,

You can install java 5 by doing the following

```
sudo apt-get install sun-java5-jdk
```

and similarily install java 6 with

```
sudo apt-get install sun-java6-jdk
```

To select which version of java the system uses you can use:
```
sudo update-alternatives --config java
```

You probably want to keep using java 6 on your system. To update the jvm being used by eclipse you can add a new jvm to Window->Preferences->Java->Installed JREs. Add the new JVM and make it the default. Also set your project compliance level to 5 by setting Project->Properties->JDK Compliance to 5.0

Ubuntu installs jvm's to /usr/lib/jvm by the way

---

### Post by xlinuks on 2008-01-18
Since I don't work with Eclipse i can help installing another JDK: just download the "bin" version from Sun and you're done. I always download the "bin" versions to be able to easily swtich between them.

---

### Post by sagarhshah on 2008-01-18
Thanks for the replies.
Tried what kevykev said to do and it works.

Thanks man

Sagar

Marked thread as solved to help others who might have a similar problem

---

