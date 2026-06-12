---
title: "Help with a JOIN query needed mysql 4.1"
date: 2008-04-20
forum: Programming Talk
---

### Post by wrightee on 2008-04-20
Hi - I'm sure this can be done with one query but it's driving me nuts!  I have something like this:

tbl_people:
- id, name

tbl_comments:
- id,people_id,comment,dated

I want to select all people and their latest comment.  If I do something like:

select name, max(dated) as d comment, from tbl_people left join tbl_comments on tbl_people.id=people_id group by name

.. I get (normally) the earliest comment.

Could someone please advise?  Thanks in advance.

---

