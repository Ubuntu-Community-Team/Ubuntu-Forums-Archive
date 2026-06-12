---
title: "Urgent : Java web application data base error"
date: 2008-10-02
forum: Programming Talk
---

### Post by umshiva on 2008-10-02
Hi experts ,

I want to connect web application server(TOMCAT) to ORacle 10g

Presently we are using 9i database and this is getting migrated

We changed the config.ini and data-source.xml files correctly in order to connect to the 10G database.

still it is getting connected with 9i databse only.
Whehter we should change any other files.

I do not have sessions.xml file in my server. should i create this to resolve this problem.

When i am conecting the oracle 10g on toad its gives 
**Can't initialize OCI : error -1 **

Please help me in this.

Lot of thanks in advance

---

### Post by The Cog on 2008-10-03
The only thing I can think of is that perhaps the drivers for 9i and 10g are different. The drivers go (IIRC) in jvm/lib/ext. Worth checking perhaps.

---

