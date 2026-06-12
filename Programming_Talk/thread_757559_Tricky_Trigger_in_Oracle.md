---
title: "Tricky Trigger in Oracle"
date: 2008-04-17
forum: Programming Talk
---

### Post by kamasabi on 2008-04-17
gents,

Anyone have some experience with SQL and triggers? Attempt:

I have a table, for instance tutor, that has a TutorID that I want to auto increment, however, it is a char string, in this case, t001, t002, etc. If it were simply a number, it wouldn't be an issue. So, what I want to do....

I want to make a trigger or stored function that breaks that char into 2 segments: the character and the numbers, then increment the numeric part, and then piece the two back together.

Or if there is an easier method of doing this, that'd be cool too :)

here is the actual table creation entry:

> CREATE TABLE Tutor (
  TutorID char(4) NOT NULL,
  TutorMajor VARCHAR(40) NOT NULL,
  TutorName VARCHAR(40) NOT NULL,
  TutorAddress VARCHAR(50) NOT NULL,
  TutorPhone number(10) NOT NULL,
  TutorEmail VARCHAR(50) NULL,
  PRIMARY KEY(TutorID)
);

Any ideas? Working in Oracle 10g Express.

-Kama

---

### Post by [h2o] on 2008-04-17
Not a solution, but a question: Do you _really_ have to store the tutor id as a char?
Will there be other id-types than "t"+integer, like "r102" or "b009"?

Otherwise you might get away with storing the id as an integer and then either
1) Adding a "t" everytime you print it in your client application code.
or
2) Make a view that automagically appends "t" to id and let your application code use that view to get the data. That's probably a better choice than (1).

---

### Post by nick_h on 2008-04-17
In Oracle, you should consider using a Sequence to generate an incremental ID.

---

### Post by kamasabi on 2008-04-17
aye, there are several others like that, but for different tables.  Here is a link to my data model:

[http://img169.imageshack.us/img169/7471/datamodelvv8.png](http://img169.imageshack.us/img169/7471/datamodelvv8.png)

most tables have their own ID similar to that one, so for labs it would be l001, or supervisors s001, etc.  

I think I recall looking around online about making a sequence, I'll take a look and see if I can figure out how to do it.

---

### Post by nick_h on 2008-04-19
> think I recall looking around online about making a sequence, I'll take a look and see if I can figure out how to do it.

Just google for "oracle sequence" - you will get a lot of links.

For example - [link](http://www.databaseanswers.com/sql_scripts/ora_sequence.htm) - is nearly what you want.  You will need to add the letter to the front of the ID.

---

### Post by pmasiar on 2008-04-19
If all IDs in thattable have a 't' prefix, it is really needed to store it? Will you use it as a foreign key, where IDs from other tables can be stored as well? Maybe better idea will be to have 'ref_type' in that other table (with value 'tutor' or 't'). Seems like 't' is just a magical value which you plan to interpret somehow later. This kind of hidden magic is poisonous, IMHO.

In table tutor you know you have all ts, you may as well having calculated column adding it to ID.

---

### Post by Boodah on 2008-04-20
I agree, the 't' prefix is redundant if all Tutor records are prefixed the same. Remove the 't' and use a regular sequence number.

If your concern is application presentation then in the SQL Select on that table, do a Select 't' || TutorID as TutorID to present the prefix.

It's never a good idea to overload columns in a database, they'll usually bite you later : -)

---

