---
title: "JRE Firefox"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by brunoskrebs on 2008-07-09
Hi I cant manage to put jre working on firefox.

I have jre and jdk as well, because Im programming with java. But when I access a site that was supposed to show an applet it doesnt.

And it is a very important site to myself.

Can someone help me?

Thanks in advance.
Bruno Krebs

---

### Post by gila_monster on 2008-07-09
Without knowing more about your system, I'd guess that you have sun-java6-bin and sun-java6-jre installed, but not sun-java6-plugin. Check synaptic and see if you have the plugin. If you don't, install it and try your site again and let us know how it works out.

---

### Post by stchman on 2008-07-09
> **brunoskrebs said:**
> Hi I cant manage to put jre working on firefox.

I have jre and jdk as well, because Im programming with java. But when I access a site that was supposed to show an applet it doesnt.

And it is a very important site to myself.

Can someone help me?

Thanks in advance.
Bruno Krebs

Do you have 32 or 64 bit installed.  if 32 then do the following:

```
sudo apt-get install sun-java6-plugin

```

For 64 bit you will need to use Icedtea.  All the other SUN Java stuff runs fine in 64 bit BUT the browser plugin.  Remove SUN Java and install the following.

```

sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

---

### Post by brunoskrebs on 2008-07-10
Yeah sun-java6-plugin missing.

Thanks people...

---

