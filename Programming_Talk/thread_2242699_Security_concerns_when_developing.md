---
title: "Security concerns when developing"
date: 2014-09-03
forum: Programming Talk
---

### Post by Zirts on 2014-09-03
Hi!

So I am developing a Ruby on Rails web application on my desktop computer and also on my laptop. Currently on both of them I have postgresql and Passanger with apache installed and running for the application. But I am wondering, is there a big point of using them in the development stage? WIl running Apache2 server on my desktop computer not open pointless security concerns and also take away lot of resources? Would it be smart to only use them when the application goes to production. But then again, what else would I use during development.

---

### Post by ofnuts on 2014-09-03
Well, If you have security concerns with your Apache server on your development PC, why wouldn't you have them too on the production system? Normally if you have secured your personal systems with properly configured IPTables, there should not be any problem. If you aren't running a server on your development system, you can only run small unit tests... Also, depending on the "production" system, you could need a real test system with a configuration as close as possible to the production ones.

---

