---
title: "Relating Two Tables (MySQL)"
date: 2012-12-22
forum: Programming Talk
---

### Post by kevinharper on 2012-12-22
I have 2 tables: users & access_levels.

users has 5 columns: id, user_name, password, full_name, active
access_levels has 3 columns: id, access_level, active

I have a couple of options on how to join these.
1) add a "access_level_id" column to the users table and then JOIN when querying ON access_levels.id=users.access_level_id
2) create a third table (join_users_access_levels) with two columns: user_id, access_level_id.

Which method do your prefer? I am currently implementing the 2nd. But my 'joins' look like this:
```
SELECT *
   FROM users, access_levels, join_users_access_levels
WHERE users.id=join_users_access_levels.user_id
   AND access_levels.id=join_users_access_levels.access_level_id
```
This can easily get out of hand.

Is there a way to JOIN the users, access_levels, and the join_users_access_levels tables without adding an extra column to the users table?

---

### Post by Bachstelze on 2012-12-23
You should use 1). As you have noticed, three tables are a lot more complicated than two since you need to do tho equality tests.

---

### Post by kevinharper on 2012-12-23
I was reading a whole lot after I posted the OP.

Here's a summary of what I read:
There are basically three types of relationships. The first 2 I'll list should use the first relationship (2 tables), and the 3rd should use the second relationship (3 tables).

Types:
1) 1 item from the first table is related to exactly 1 item from the 2nd table. (use 2 tables)
2) 1 item from the first table is related to many items from the 2nd table. (use 2 tables)
3) Many items from the first table are related to many items on the 2nd table. (use 3 tables)

But is this right? Bachstelze, you're right because I have a 1-to-1 relationship. But what about when there is a 1-to-many or a many-to-many relationship? I would NEED 3 tables in those cases, right?

---

### Post by Bachstelze on 2012-12-23
Yes, in your case 3) would arise if a user could have several access levels.

---

### Post by SeijiSensei on 2012-12-23
In your case is there even any reason to have a second table?  Why not just add access_level as a field to the first table and have one record per user?  Is there a situation where "active" has different values in the two tables?

---

### Post by kevinharper on 2012-12-23
> Yes, in your case 3) would arise if a user could have several access levels.
Never the case. I will definitely alter the users table to include an access_level_id that corresponds to access_levels.id.

> In your case is there even any reason to have a second table?
A couple of reasons. I want to have the flexibility of adding or disabling access levels.

> Is there a situation where "active" has different values in the two tables?
These are separate form one another. Because the id's for both tables are autoincrements. I want to have a way to disable (active=0) a row without having to remove it, out of fear of one day running into corruption issues.

---

### Post by KdotJ on 2012-12-23
I'm a little with SeijiSensei on this one...

If you are not going to have a massive database, then it's sometimes easier to just be simple.

I wouldn't necessarily introduce a second table "just because you can". Yes in the real world on large database architectures, this is the proper way to go with normalisation, But you already know that. 

Just having the access level as an attribute on the main table is simpler and requires no joins or nested selects when executing simple queries.

---

### Post by Bachstelze on 2012-12-23
> **kevinharper said:**
> 
These are separate form one another. Because the id's for both tables are autoincrements. I want to have a way to disable (active=0) a row without having to remove it, out of fear of one day running into corruption issues.

InnoDB cross-table references might help you there (in this particular case, it will refuse to delete an access_level row if there are users "using" it).

---

### Post by kevinharper on 2012-12-23
@KdotJ
Thank you. I've decided to go through w/ 2 tables.

> I wouldn't necessarily introduce a second table "just because you can". Yes in the real world on large database architectures, this is the proper way to go with normalisation, But you already know that
I am all about simplicity. I am confident I can program just about anything I need. But it might just be a nasty hack. I would probably get banned from this forum if I were to have my code audited. :) Okay, not that bad... but it can be awful at times.

You'll notice that most of my questions are about improving things that I have already done. I will usually go a full 12 rounds with a problem before asking for help. Doing so helps me learn and I am better able to comprehend the answers/suggestions I get from others afterwards.

Although in this particular project my users and access_levels tables may never grow to a million records, I would like to set it up with the ability to accommodate such an expansion/growth.

Thanks all for your responses.

---

