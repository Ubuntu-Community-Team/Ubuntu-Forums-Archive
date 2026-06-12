---
title: "My Application Server (BEA Weblogic) cannot able to access MySql Driver"
date: 2006-12-29
forum: Programming Talk
---

### Post by SwaroopKunduru on 2006-12-29
Hi All,

I installed MySql java driver locally and I am running BEA Weblogic server as SUDO. Where I have to place the Database (MySql) jar file so that my BEA Weblogic can access.

I am getting an exception saying driver not found. I can access driver through java program run locally.

Regards,

Swaroop Kunduru.

---

### Post by lloyd mcclendon on 2006-12-29
this is a guess but drop it in the websphere dir/common/lib

that's where it goes for tomcat & i'm pretty sure most java app servers are similar when it comes to stuff like this.

you coudl google for where to put jdbc driver websphere and i'm sure you'd find it

---

