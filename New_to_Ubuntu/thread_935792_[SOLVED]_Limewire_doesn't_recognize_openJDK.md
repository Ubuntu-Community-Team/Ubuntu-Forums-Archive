---
title: "[SOLVED] Limewire doesn't recognize openJDK"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by koba101 on 2008-10-02
Hi,

I was trying to install the basic limewire package on hardy,

I got this message:

```
dpkg: dependency problems prevent configuration of limewire-basic:
 limewire-basic depends on sun-java6-jre | icedtea-java7-jre | sun-java6-jdk | icedtea-java7-jdk | sun-java5-jre | sun-java5-jdk; however:
  Package sun-java6-jre is not installed.
  Package icedtea-java7-jre is not installed.
  Package sun-java6-jdk is not installed.
  Package icedtea-java7-jdk is not installed.
  Package sun-java5-jre is not installed.
  Package sun-java5-jdk is not installed.

```


it's looking for sun-java6-jre, but I've got openJDK installed


this isn't the only installation that didn't recognize it, i had a problem with a php-java-bridge as well


what do i  do here?

---

### Post by kostkon on 2008-10-02
> **koba101 said:**
> Hi,

I was trying to install the basic limewire package on hardy,

I got this message:

```
dpkg: dependency problems prevent configuration of limewire-basic:
 limewire-basic depends on sun-java6-jre | icedtea-java7-jre | sun-java6-jdk | icedtea-java7-jdk | sun-java5-jre | sun-java5-jdk; however:
  Package sun-java6-jre is not installed.
  Package icedtea-java7-jre is not installed.
  Package sun-java6-jdk is not installed.
  Package icedtea-java7-jdk is not installed.
  Package sun-java5-jre is not installed.
  Package sun-java5-jdk is not installed.

```


it's looking for sun-java6-jre, but I've got openJDK installed


this isn't the only installation that didn't recognize it, i had a problem with a php-java-bridge as well


what do i  do here?
You could install the Sun Java; the package is called *sun-java6-bin*.

Then, you'll have to set it as the default Java for your system, by opening a terminal and doing
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by bangeko on 2008-11-11
For php-java-bridge, just deploy JavaBridge.war file distribution. Rork for me.

---

