---
title: "PostgreSQL - Mono problem"
date: 2007-04-12
forum: Programming Talk
---

### Post by bkopanja on 2007-04-12
Hi everybody!

Yesterday i installed MonoDevelop and I was amazed how great IDE it is :). Then I tried to add a support for Postgre databases and I installed Npgsql v1 and v2 through apt-get, but when I try to include Npgsql in my project debuger tells me that it can't find Npgsql on my computer... I checked and Npgsql is present at /usr/lib/mono/gac so I don't know what's the problem... 

Is there anything I need to do to tell to teh IDe where is that file or is there something else that's bothering me :D.

Thanks in advance!

Bojan Kopanja

---

### Post by bkopanja on 2007-04-12
Hehe, I solved the problem :D... I just wasn't familiar with that how to add new assembly in project in MonoDevelop. 

I just should right click on References in Solution window and click Edit References... and thare it was :D. I added Npgsql, and now everything works great :D...

---

### Post by skeeterbug on 2007-04-12
> **bkopanja said:**
> Hehe, I solved the problem :D... I just wasn't familiar with that how to add new assembly in project in MonoDevelop. 

I just should right click on References in Solution window and click Edit References... and thare it was :D. I added Npgsql, and now everything works great :D...


How is the performance?

---

