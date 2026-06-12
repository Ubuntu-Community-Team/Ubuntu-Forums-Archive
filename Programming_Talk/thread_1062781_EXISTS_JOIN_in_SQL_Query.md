---
title: "EXISTS/ JOIN in SQL Query"
date: 2009-02-07
forum: Programming Talk
---

### Post by s.fox on 2009-02-07
Hi,

I am experiencing some real trouble with some SQL.  I have 4 tables that are structured as follows:

**user**;

userID
userForname
userSurname

**group**:

groupID
groupName

**resource**:

resourceID
resourceName
resourceOwner

**groupResource**:

groupID
resourceID

Basically the problem is this:  

A user can share resources with groups that they belong to.  They can only share resources that they own.  If a resource is shared it appears in the groupResource table.  I want to produce a list of resources shared to a particular group that a certain user owns.  I would also like to reverse the query and produce a list of resources that have not been shared by a particular user to a certain group.  I think I need to use a JOIN and also maybe a EXISTS in my sql.  All the ID's are numerical.

I really stuck and getting nowhere slow.  If anyone can help me out or point me in the right direction I would be very grateful. If any clarification is needed please don't hesitate to ask.

-Ash R

---

### Post by unutbu on 2009-02-07
How do we know when a user belongs to a group?
Some example data might help.

Also, you might run into trouble having a table named "group". At least on MySQL, it appears a query like "select * from group" will generate an error because group is a reserved word.

---

### Post by s.fox on 2009-02-07
Hi,

I forgot to mention i have a table userGroup.  This table contains 2 columns userID and groupID.  It shows which users belong to which group.  I have attached in this post some sample in the correct table structure.

I think I need to use some sort of join to ackomplish my goal,  but I am really not sure. 

Thank you for taking an interest in this problem i am experiencing.

---

### Post by s.fox on 2009-02-07
Good news!

I was able to sort it out on my own.  Thanks anyway.

-Ash R

---

