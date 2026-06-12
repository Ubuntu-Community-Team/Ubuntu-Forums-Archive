---
title: "SQL: How do you deal with &quot;sometimes&quot; relationships"
date: 2008-10-20
forum: Programming Talk
---

### Post by doas777 on 2008-10-20
Howdy all. I've been thinking about a database design scenario for a while now, and was wondering how some of you folks would deal with this premise. 

I have a parent table related to several other tables in a "1-To-0..*" (one parent to Zero->many children). completely 3rd normal, but with many nullables.

The specific child table used is based on the value of a field in the parent, and it is exclusive to that table, so a parent with a type of "A" can only have children in the table "TypeA". it specifically cannot have a child in tables "TypeB" or "TypeC". if ever this happens, integrity is lost.

Here is a breif example (this is not SQL. we're not talking syntactics here):
```

TABLE Parent
	ParentID int IDENTITY(1,1) PK
	TypeID int FK references TypeLookup.TypeID
	...

TABLE TypeAChild
	TypeAChildID int IDENTITY(1,1) PK
	ParentID int FK References Parent.ParentID
	... <TypeA stuff. very differant from typeB stuff>

TABLE TypeBChild
	TypeBChildID int IDENTITY(1,1) PK
	ParentID int FK References Parent.ParentID
	... <TypeB stuff. very differant from typeA stuff>

Table TypeLookup 
	TypeID int IDENTITY(1,1) PK
	Typename varchar


```

Now, if the Parent type value is 0 (for 'A') then the relationship points to TypeAChild, whereas for parent.type = 1 ('B'), the relationship points to TypeBChild. so how would you go about enforcing constraints on that relationship? not only must the parent row exist, but it must be of the correct typeValue.

I've come up with a few ways to do it, but all of them have some downsides. I want to do this all in SQL (though yes, a well written interface app would play by the rules).

1) use triggers to undo the update if the val fails. 
downside, error handling within triggers is clumbsy to pass up to the application, and I already have history-ing triggers on update and delete. upper tier apps would have to add more code for child inserts, parent updates, and exception handling all the way up the stack if the trigger rejects the row after insert.

2) denormalize the parent table into ParentTypeA and ParentTypeB. then I could have hard relationships between the two, and parent is mostly lookupIDs so not a lot of data duplication. Would also get rid of extra nullables on the parent that are "type" specific.
downside, I have broken 1st form normalization.the database is (slightly) larger and more complex. upper layer applications will have to implement extra code to accomodate inserts, updates, and deletes. also might not be 100% effective in preventing bad recs, when using autonumber keys.

so how would you folks deal with this scenario?

Cheers,
Franklin

---

### Post by jflaker on 2008-10-20
Joins, but they confuse me....

In a customer/order situation, you may have many customer without historical orders.....

Order/OrderDetail situation......is an ALWAYS situation....

It gets confusing when you have customer/Order/OrderDetail

---

### Post by doas777 on 2008-10-20
I don't quite follow you. Joins would help in retrevial, and I guess i could use updatable views for inserting the first child,  but the multiplicity isn't really right for it I think. could you expound a bit? I'm likely missing your gist.

---

### Post by fballem on 2008-10-20
I suspect that there is a tendency to confuse data integrity rules with business rules. In past lives, database rules were often used to enforce business rules, but things change.

I'd like to suggest:

The relationships between Parent and each of the children are straight foreign keys. In order for an entry to exist in any of the children, there must be an entry in the Parent. This is a straight forward data integrity rule.

The fact that a Parent must be of Type A in order to have an entry in Type A, and there should be no entry in Type B is a business rule and should be enforced within your application. The reason for this is that business rules have a nasty habit of changing, and it is easier to change the business rule in the business layer of your application. If you do try to enforce it in the database, then you will have to make a change in at least two places (the business layer and the data layer).

As you have already discovered, the building of the business rule into the database is complex. By experience, I will also tell you that it is prone to error and harder to maintain.

Hope these thoughts help,

---

### Post by doas777 on 2008-10-20
That's very sage advice fballem. You make an excellent point. That is exactly the kind of thing the data access tier is for. Thank you!

Any further discussion on the topic is welcome. I'm interested in a wide variety of thoughts on the matter.

Have fun,
Franklin

---

### Post by pp. on 2008-10-21
My SQL has become a bit rusty and wasn't too robust to begin with.

However, I think it ought to be possible to define for every 'child' table Ci a view Vi such that Vi defines a join (Ci -> Parent) with the requirement that Parent.type = i.

Since Parent.type can have one and only one value, this guarantees that for every tuple in Parent there can be Tuples in at most one Child table.

The mechanism does not guarantee that there are any Child tuples at all for any given Parent tuple.

That would require an additional view (Parent -> Ci) where Parent.type = i with the requirement that Ci exists. I am, however, quite unable to tell whether there is such a construct in SQL. (Been a very long time, indeed)

---

### Post by fballem on 2008-10-21
In some dialects of SQL, you can update a View, although there are limitations. Not sure how this is done, but might be worth looking into if you are insistent on putting business logic into the data layer.

Regards,

---

### Post by mike_g on 2008-10-21
Personally I would use another programming language to handle the logic. It would be much simpler. 

Edit: why not use an if statement?

maybe something like:
```
  CREATE PROCEDURE INSERT_THING(data TEXT, type SMALLINT)
  LANGUAGE  SQL
  BEGIN
    IF type = 0 THEN
      UPDATE parent ...
      UPDATE childA ...
    ELSEIF type = 1 THEN
      UPDATE parent ...
      UPDATE childB ...
    ELSE
      UPDATE parent ...
      UPDATE childC ...
    END IF;
  END
```

---

### Post by doas777 on 2008-10-21
Thats a good point mike_g. I do use procedures to do most of my processing via sql. 

In this case I've been more worried about constraints just to protect the DB from me (or gasp, another developer...). You're quite right though, it would almost HAVE to be enforced higher up in the architecture, whether it be in a procedure or in compiled code. I guess the DB will just have to quake in fear when I am near. lol.
Thanks!
Franklin

---

### Post by brentoboy on 2008-11-18
I would, as already suggested, allow the enforcement to lie in the business application logic layer.

But, I might add that you could have a series of joins that you could run on a regular basis (nightly) that should come up with no records.

such as
```

create view mismatched_records
select p.id as id
, 'A' as expected_type
,  p.type as actual_type
from parent_table p
join child_a ch 
on p.id = ch.id
where p.type <> 'A'
union all
select p.id as id
, 'B' as expected_type
, p.type as actual_type
from parent_table p 
join child_b ch 
on p.id = ch.id
where p.type <> 'B'
select p.id as id
, 'C' as expected_type
, p.type as actual_type
from parent_table p 
join child_c ch 
on p.id = ch.id
where p.type <> 'C'

```

Then use the results from that view as a sort of debug list.  Then, you just fix the anomalies and hunt down the code in your model layer that did the nasty deed.

I would do it this way unless it is absolutely business critical that there is never a mixup, in which case you need an on insert and an on update trigger that verifies it before it ever gets in there.

---

