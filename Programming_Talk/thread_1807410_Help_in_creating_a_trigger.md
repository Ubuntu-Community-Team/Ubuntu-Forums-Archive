---
title: "Help in creating a trigger"
date: 2011-07-19
forum: Programming Talk
---

### Post by vjohnny8 on 2011-07-19
[INDENT]Hi,

I need to create a trigger for the below case:

index_id Time_vertex_id date rate pre_rate
4 1 17-06-2011 4.7 6.4
4 1 16-06-2011 6.4 7.4
4 1 14-06-2011 7.4 
4 1 15-06-2011 8.4 7.4

the index_id and time_vertex_id will be unique and when the date is 17th i.e the first date will be inserted the current rate will be 4.7 and the previous rate will be blank and when another date is inserted i.e 16th the previous rate of 17th will be the current rate of 16th i.e 6.4.

when 14th is being inserted, the previous rate of 16th will be the current rate of 14th i.e 7.4 and if after 14th is being inserted, 15th is being inserted, then the previous rate of 16th should be updated as per the current rate of 15 say 8.5.

Kindly help !!!! 
[/INDENT]

---

