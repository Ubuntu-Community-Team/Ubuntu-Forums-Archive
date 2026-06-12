---
title: "2-dimentional array as normaled table?"
date: 2008-02-20
forum: Programming Talk
---

### Post by altonbr on 2008-02-20
I haven't taken Computer Science, so please bare with me.

If I have a table that has repeating information for the two columns, such as:
```
  a b c
a x 4 6
b 4 x 9
c 6 9 x
```

x = NULL

How would I put that into a table (or multiple tables if normalized)?

> **distance_mapping**
id
location1_id
location2_id
distance

**locations**
id
name

isn't exactly normalized, is it?

---

### Post by altonbr on 2008-02-20
For sports fans, you could think of it as having a table of teams and a second table of games. The two teams have to play each other, but you don't want to be able to enter in data that could be identical (but in reverse) or have NULL data (where a team plays itself).

---

### Post by stroyan on 2008-02-20
It seems like you want a single table with a key of made by concatenating two city names.
Sorting the two city names would produce a single unique key for each pair.

You would access it with-
if (name1 == name2)
   result=NULL
else if (name1 < name2)
   result=distances(name1_name2)
else
   result=distances(name2_name1)

---

### Post by altonbr on 2008-02-20
> **stroyan said:**
> It seems like you want a single table with a key of made by concatenating two city names.
Sorting the two city names would produce a single unique key for each pair.

You would access it with-
if (name1 == name2)
   result=NULL
else if (name1 < name2)
   result=distances(name1_name2)
else
   result=distances(name2_name1)

Yes, I understand that concept, I have just not performed populating a database with this sort of data.

The problem I have is that location A in proximity to location B is the same as location B's proximity to location A. Also, location A has no, or NULL proximity to location A.

How do I set up my database to make sure these collisions do not occur? How do I mark location A's proximity to location B's without entering duplicate information (which could then lead to malformed data, especially if the numbers do not match)?

---

### Post by pmasiar on 2008-02-20
What language? Do you need to use database? How do you want to use it: what methods do you expect in the API?

---

### Post by nick_h on 2008-02-20
> How do I mark location A's proximity to location B's without entering duplicate information
When you write a function to populate the table you make sure you only enter data where location1 > location2 as previously suggested.  Then you can do the same when you write a function to get the distance.

> How do I set up my database to make sure these collisions do not occur?
If you want to enforce such a rule within a database then you need to look at adding a column constraint to the table.

---

### Post by altonbr on 2008-02-20
> **pmasiar said:**
> What language? Do you need to use database? How do you want to use it: what methods do you expect in the API?

I'll be using PHP 5.2 and MySQL 5.0

Yes I will need a database because this table of data will need to be manipulated every so often, especially as new locations are added.

I'll be using this data to record travel expenses for this company's employees. It will record that locations they went to and from what location, including the price per kilometre they should be paid. There will also be an administration section to edit all of the data, including price paid per kilometre.

---

