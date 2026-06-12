---
title: "Is this database normalized properly? (pic inluded)"
date: 2009-01-26
forum: Programming Talk
---

### Post by thenetduck on 2009-01-26
Hi 
Trying to normalize a database: [www.d3fy.com/database.pdf](www.d3fy.com/database.pdf)
Is it done correctly? 

Thanks
The Net Duck

---

### Post by kjohansen on 2009-01-26
you have the relationships set up but I do not see any foreign keys...

---

### Post by thenetduck on 2009-01-27
I'm new to this, what would be an example of a foreign key?

---

### Post by slavik on 2009-01-27
I am not a DB expert by any means, but in this example, what's the point of the linking tables? seems to me like there will have to be more indexing going on and more joins happening ...

why not have user_id and song_id in the comments table and a user_id in the songs table?

---

### Post by Reiger on 2009-01-27
Using Common Sense (tm):

A user may have zero (just signed up) or more songs in his collection.
A song may have been collected by 1 or more users. This means a user_id does not mape to a song_id one to one or onto. Which would, Slavik, incur data redundancy if you included a user_id in the song table -- seeing as for each user_id a copy of all song data would have to be stored in that case...

A comment however, can be made only once about only one song_id by only one user_id. That is, a comment_id maps one to one and onto both a song_id and user_id. (Unless, the comment could be made about a specific user rather than about a specific song -or vice versa- in which case you'd have 2 different comment tables --no?) That means there is no reason to split the comment table into subtables.

---

### Post by Reiger on 2009-01-27
> **thenetduck said:**
> I'm new to this, what would be an example of a foreign key?

Foreing keys are keys (a combination of sub-tuples which together form a unique sub-record within a table) in outside data. That is: Foreign keys are candidate keys to other tables.

In other words a user_id included within a comment table is not just interesting data; it is a foreign key to the user table. Which makes it easy to implement "send e-mail to author of comment 1234567" like functionality.

---

