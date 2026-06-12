---
title: "[SOLVED] which sun-java version - Gutsy firefox"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by wpshooter on 2008-05-27
Which version (5 or 6) of Sun-java plugin should I install with Gutsy/firefox ?

Thanks.

---

### Post by steveneddy on 2008-05-27
You might want to look at iced-tea before you install anything java.

```

sudo apt-get install icedtea-gcjwebplugin icedtea-java7-jre icedtea-java7-plugin

```

---

### Post by iaculallad on 2008-05-27
> **wpshooter said:**
> Which version (5 or 6) of Sun-java plugin should I install with Gutsy/firefox ?

Thanks.

The more updated the version of SunJava you use, the better. Use version 6 update 6

---

### Post by wpshooter on 2008-05-27
> **steveneddy said:**
> You might want to look at iced-tea before you install anything java.

```

sudo apt-get install icedtea-gcjwebplugin icedtea-java7-jre icedtea-java7-plugin

```

When I look at the description of this iced-tea in Synaptic I notice the word "temporary".  What is the significance of that ?

Thanks.

---

### Post by steveneddy on 2008-05-29
> **wpshooter said:**
> When I look at the description of this iced-tea in Synaptic I notice the word "temporary".  What is the significance of that ?

Thanks.

iced-tea works better for many people than regular JAVA.

Use it until JAVA gets better.

I am. works great.

---

### Post by stchman on 2008-05-29
> **wpshooter said:**
> Which version (5 or 6) of Sun-java plugin should I install with Gutsy/firefox ?

Thanks.

32 bit do the following.

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

This will install 1.6 Java.

---

