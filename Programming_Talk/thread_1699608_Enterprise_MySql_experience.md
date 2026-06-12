---
title: "Enterprise MySql experience"
date: 2011-03-03
forum: Programming Talk
---

### Post by foxmuldr on 2011-03-03
Does anybody have experience with MySql in an enterprise environment? How does it do compared to other commercial systems?  Is is reliable?  Desirable?

I ask because:
I'm considering migrating two dedicated IBM AS/400 DB2 machines to a newer MySql machine. We have about 50 users querying data around 30 tables which have from 1 to 200,000 records each, typically about 30,000 records.

Under max loads our users query maybe one or two SQL commands per second, though typically more like every two to 10 seconds.  Our facility operates continuously (24 hours per day and five or six days per week).

Thanks in advance.

- Rick C. Hodgin

---

### Post by DaithiF on 2011-03-04
Hi, I don't think that level of load sounds too taxing ... MySQL should cope fine.

---

### Post by Some Penguin on 2011-03-04
Shouldn't be a problem unless you have complex queries or are writing to data hotspots and thus expecting to be rolling back frequently.  I'm pretty sure I've had individual MySQL tables well in excess of 2M rows in rapid write-heavy but low-collision workloads (crawling-related) -- this was a while ago so my memory's vague.  Using PostgreSQL now, which holds up pretty well under similar scales.

---

