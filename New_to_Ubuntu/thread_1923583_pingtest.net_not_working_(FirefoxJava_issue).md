---
title: "pingtest.net not working? (Firefox/Java issue)"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by d4m1r on 2012-02-10
Wow, I've made several topics about different issues tonight but here is another...Is pingtest.net actually working for anyone running Firefox 10? It wasn't running in Firefox 9 either actually, and I do have Java installed....

It just tries to send and receive packets but first it must launch a java applet which it seemingly never does and the test goes on forever....On that note, how do I check if Firefox is using OpenJDK, Icedtea, or the Sun package as it seems I have all 3 installed :confused:

---

### Post by ikt on 2012-02-11
> **d4m1r said:**
> Wow, I've made several topics about different issues tonight but here is another...Is pingtest.net actually working for anyone running Firefox 10? It wasn't running in Firefox 9 either actually, and I do have Java installed....

It just tries to send and receive packets but first it must launch a java applet which it seemingly never does and the test goes on forever....On that note, how do I check if Firefox is using OpenJDK, Icedtea, or the Sun package as it seems I have all 3 installed :confused:

It only needs java for packetloss testing.

There is some information here on installing java and the java browser plugin:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I would remove all 3 packages and then reinstall and just use OpenJDK/Icedtea.

---

### Post by d4m1r on 2012-02-11
> **ikt said:**
> It only needs java for packetloss testing.

There is some information here on installing java and the java browser plugin:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I would remove all 3 packages and then reinstall and just use OpenJDK/Icedtea.

Ok. Does it work for you? Which package do you use and browser?

---

### Post by d4m1r on 2012-02-17
Still an issue with Firefox 10 and **Version 6 Update 23.**

---

### Post by d4m1r on 2012-02-28
Just an update that pingtest.net is working for me now with Firefox 10.0.2 and Java 6 Update 23.

The trick was to disable the IcedTea Firefox plugin and to manually install the official Java JDK according to this guide:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

