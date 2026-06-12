---
title: "netbeans slow performane!"
date: 2010-09-02
forum: Programming Talk
---

### Post by margemoosh on 2010-09-02
I have problems with netbeans 6.8 in ubuntu lucid, its too slow comparing to other applications i searched and i think the problem is in not using opengl in java(something like that) i tried everything i found in forums but nothing worked.
i added something to neatbeans.conf file but when i want to run netbeans from terminal it says ```
Unknown option -Dsun.java2d.opengl=true

```i tried installing a few packages but nothing worked!
i don't know anything about java and this option because i only use netbeans for PHP

---

### Post by margemoosh on 2010-09-04
anyone?

---

### Post by Some Penguin on 2010-09-04
Obvious question:  are you using a Sun JVM, and if so, which version?  If not, well, don't expect it to understand a Sun-specific JVM option.

---

### Post by margemoosh on 2010-09-04
> **Some Penguin said:**
> Obvious question:  are you using a Sun JVM, and if so, which version?  If not, well, don't expect it to understand a Sun-specific JVM option.

i don't know anything about java virtual machine and it's options i just need to install a package which have this option i want to use(i searched forums and someone said adding this optino will solve my problem with slow performance) but the newer problem is i can't use this option because java says it's unknown option
here is my java information:

```
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK Server VM (build 16.0-b13, mixed mode)

```

---

### Post by Some Penguin on 2010-09-04
IcedTea, then.

[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

has a fair bit of info on the various JDKs available and how to install and enable them.  That option you're looking at is Sun-specific; there may be equivalents for others, but I'm not familiar with GL support for any of the rest.

---

### Post by margemoosh on 2010-09-04
> **Some Penguin said:**
> IcedTea, then.

[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

has a fair bit of info on the various JDKs available and how to install and enable them.  That option you're looking at is Sun-specific; there may be equivalents for others, but I'm not familiar with GL support for any of the rest.

i also installed java-6-sun package.
can i switch to it and use it?
```
margemoosh@Sisto:~$   sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode


```

---

### Post by Some Penguin on 2010-09-04
> **margemoosh said:**
> i also installed java-6-sun package.
can i switch to it and use it?

Why wouldn't you be able to?  In particular, the thread that provided you the option that provoked this thread specifically mentioned using the Sun JDK.

I suppose that it's theoretically possible that you have /other/ Java packages that have dependencies on your current JVM for whatever reason, but it's fairly unlikely, and Sun's, while not bug-free, is still pretty good.

---

### Post by margemoosh on 2010-09-05
> **Some Penguin said:**
> Why wouldn't you be able to?  In particular, the thread that provided you the option that provoked this thread specifically mentioned using the Sun JDK.

I suppose that it's theoretically possible that you have /other/ Java packages that have dependencies on your current JVM for whatever reason, but it's fairly unlikely, and Sun's, while not bug-free, is still pretty good.

i'll try to purge everything related to java and reinstall needed packages.
just a question which packages should i install (consider i have a fresh new ubuntu lucid)  to be able to use this option in netbeans?

---

### Post by Queue29 on 2010-09-05
> **margemoosh said:**
> i'll try to purge everything related to java and reinstall needed packages.
just a question which packages should i install (consider i have a fresh new ubuntu lucid)  to be able to use this option in netbeans?

Don't do that, you'll end up removing everything which depends on Java as well..
Just set the default to the sun jvm like you were about to do in your previous post. Or you could just remove the openjdk, and the default will be set to the (only remaining) sun jvm automatically.

---

### Post by margemoosh on 2010-09-05
> **Queue29 said:**
> Don't do that, you'll end up removing everything which depends on Java as well..
Just set the default to the sun jvm like you were about to do in your previous post. Or you could just remove the openjdk, and the default will be set to the (only remaining) sun jvm automatically.
i uninstalled open jdk but the problem is not solved.
i installed netbeans from repositories and this option works but the problem is php is not installed by default on it and as sun doesn't let people from my country access anything in their website i can't install php on it so i asked a friend of mine in another country to download it and send it to me but when i install this netbeans.sh file which contains php support i get this Unknown option -Dsun.java2d.opengl=true
i think the problem is in netbeans home directory.
anyway testing repository version with this option shows it's still slow. ishould search to find another way to speedup netbeans
thanks to all who tried to help me

---

