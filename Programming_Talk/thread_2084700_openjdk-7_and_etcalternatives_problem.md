---
title: "openjdk-7 and /etc/alternatives problem"
date: 2012-11-16
forum: Programming Talk
---

### Post by mneisen on 2012-11-16
Hi all - I run a server on Oneiric; I need to upgrade to OpenJDK 7.

I have installed openjdk-7-jdk, openjdk-7-jre-headless and some more openjdk-7* packages without problems. 

BUT: The alternatives system does not seem to pick up the new java version correctly. 

When I do "update-alternatives -s java-1.7.0-openjdk", I get this output: [http://pastie.org/5386823](http://pastie.org/5386823) . 

Does anyone has any idea how to do this correctly (nd yes, I know about update-alternatives -install)?

Thanks in advance!

---

