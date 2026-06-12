---
title: "Java: migrating from GlassFish to tomcat 6"
date: 2009-02-02
forum: Programming Talk
---

### Post by rogier.de.groot on 2009-02-02
Hi everyone, I was wondering about something. Since I only use my GlassFish server to host JSF web applications and web services backed by a database, I figured I could migrate to tomcat6 which would consume fewer resources, right?

Using JSF and JPA on tomcat 6 is possible right?

But I can't figure out which jars to include in tomcat's lib directory to make this happen. And if eclipse would detect those jars if I did so I don't have to include them in every project.
Also, I'm not entirely sure if JPA will work since tomcat doesn't support transactions and entitymanager injection.

Does anyone know how to do this? Google isn't helping to much (finds too much junk).

---

### Post by txcrackers on 2009-02-03
I don't know about how resource heavy either one of those app servers are. I supposed GlassFish would be a bit hefty, but you could probably turn off the vast majority of the stuff you're **not** using.

But, there's a couple of fairly easy ways to do this: using Hibernate and/or Spring. I also seem to vaguely remember that Tomcat was introducing a Transaction manager, but I (quite frankly) haven't been paying to much attention (currently using Jetty, Spring, Hibernate Annotations).

---

### Post by cl333r on 2009-02-03
Goolge for "Tomcat jsf" and alike, lots of stuff. You should really ask if you googled first, failed and ask for troubleshooting.

---

### Post by rogier.de.groot on 2009-02-03
Thanks for the info; I was looking at spring already. As for Hibernate, I really don't care which JPA implementation I use, but I heard EclipseLink was faster.
I did a lot of googling on the subject, but most of the stuff it finds are people having problems doing this...
Anyway, txcrackers, do you use some sort of spring weaver to get the resource injection working?

---

