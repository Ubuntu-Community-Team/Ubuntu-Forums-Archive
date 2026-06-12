---
title: "Best HA - High Availability solution"
date: 2019-05-16
forum: New to Ubuntu
---

### Post by mrhappybunny on 2019-05-16
So i've been looking for a good solution for my Ubuntu problem.

I've seen and worked with a lot of outdated programs and some are just getting more and more advanced.

I worked with 

HA.
Pacemaker.

Is there any good solution to make Ubuntu into a Clustered system?

---

### Post by oldrocker99 on 2019-05-16
How many machines do you want to cluster? If you only have one machine, there's no cluster available. Here's how to set a domain:

[https://kerneltalks.com/howto/how-to-setup-domain-name-in-linux-server/](https://kerneltalks.com/howto/how-to-setup-domain-name-in-linux-server/)

---

### Post by TheFu on 2019-05-16
There are 50+ different types of clusters. Can you be more specific about the services?

---

### Post by mrhappybunny on 2019-05-28
Well i got 2 Ubuntu Apache/FTP servers i need to get clustered and i'm thinking about using Heartbeater as a HA cluster system.

I know pacemaker is a good one to specify if needed.

---

### Post by TheFu on 2019-05-28
Why not just use DNS round-robbin with sticky connections and run 2 servers concurrently using block replicated storage between them for any non-DBMS needs. 
If there is a DMBS, you can setup active-standby or active-active if is postgressql.  If the end-user records don't ever impact each other, like a social network server wouldn't, then slower log-based replication would be more efficient.  Just depends on the sort of DBMS records.

---

