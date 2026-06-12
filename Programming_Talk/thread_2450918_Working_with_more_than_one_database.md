---
title: "Working with more than one database?"
date: 2020-09-23
forum: Programming Talk
---

### Post by batmanfan01 on 2020-09-23
I'm programming a new app and I encountered the following problem: my server is just too small for such a huge amount of data. 
I had thought about switching my complete data chaos to an external database, but I'm afraid that this database will be too big or too small. I don't know much about that ...


Isn't there a possibility to use several databases at once? So that you connect them how? I have heard that [Aiven]("https://aiven.io/influxdb") offers this possibility. 
Have any of you ever worked with this cloud based Provider? 


I would be very grateful for all your experiences!

---

### Post by TheFu on 2020-09-23
Yes, you can use multiple databases at the same time, but don't expect to perform joins between them without a data synchronization task running externally. They are separate. Separate connections, separate queries, separate updates. separate everything.

BTW, we can't read your mind.  What database?  What language? Or are you just trying to get a link into these forums?

---

