---
title: "Zend Studio 5.5 refresh problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by graben3 on 2008-05-11
I have Zend Studio 5.5 installed under ubuntu hardy 8.04.

Everything is working well except I can't work with ZendStudio since it has a huge update problem. If I resize any panels the screen won<t refresh correctly leaving grey areas all around. See included snapshot.

Does anyone have any idea of what I should do to get that working?

The same version I installed under ubuntu haydy is the one that was working perfectly under ubuntu 7.10 before

---

### Post by graben3 on 2008-05-11
OK, I finally got it working well (not tested anything but seems OK).

What I did :

1. Got into Synaptic

Completely removed these packages :
sun-java6-bin
sun-java6-jre
openjdk-6-jre-headless
openjdk-6-jre
icedtea-java7-jre

Basically this uninstall any Java Runtime Environnment you may have installed

Then I installed into synaptic again :

sun-java5-bin
sun-java5-jre

It now works perfectly and fast but I wont be able to run a java program needing java6 so this is only a temporary fix

---

