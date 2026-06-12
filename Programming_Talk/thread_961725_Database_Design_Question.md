---
title: "Database Design Question"
date: 2008-10-28
forum: Programming Talk
---

### Post by eviltang on 2008-10-28
I am looking for more information on designing a database for a web project of mine.  I am not sure what I should be searching for (terms/phrase to use).  

This is probobly a terrible place to ask seeing that it is not related to ubuntu (directly).  But I have had such a great response to other issues I had, I thought I would start here.  

Here goes:

I would like to create a database that does something like this:

users_table:
username
email

users_friends_table:
username
friend


What I want to do is have all of the users information in one table.  Then allow the users to add friends that reference the users_table.  Its like a One to many to many relationship.  Here is a specific example:

first, there are 3 users in the users_table.
users_table:
joe
joe@localhost

john
john@localhost

kevin
kevin@localhost

second, joe has john and kevin as his friends.
users_friends_table:
joe
john

joe
kevin

I would like to get the information for kevin and john from the first table (users_table).  Thus, I am thinking it is a one to many to many relationship.  I know that I could just create multiple queries based on the results of other queries, but somehow, that seems like the wrong way.  Any input/direction is appreciated.

R/S,

Eviltang

---

### Post by mike_g on 2008-10-28
You could reduce redundancy and space usage by having the userfriends table simply storing a composite key linking users to friends. EG:
```

####USER####
uid      <-----+
username       |
email          |
password       |
               |
###FRIEND###   |
user_id -------+
friend_id -----+

```

---

### Post by Tony Flury on 2008-10-28
What you have is actually called a many to many - one user has many friends - and a user could be a friend to many other users.

The common way to model this in a relational database is to use a table which defines the relationships, so that each relationship in the database is one to many - relational databases don't handle Many to many well (without help).

Tables are therefore : 

User
username (Primary Key)
email

Friends
username1 
username2 

In the friends table both fields together form the primary key.

if you think about how this works - each entry in the User table will have many entries in the Friends table where they are username1, and also many where they are username2 - so you have got your many to many, but each row in Friends will only point to one User using username1 and one User using username2, which now means the queries are easy.

So this means it is not a million miles from what you suggested.

So the email adresses for all of "John"'s friends is 
```

Select u2.email From User as U2 WHERE (Friends.username1 = "John" and u2.username = Friends.username2) OR (Friends.username2 = "John" and u2.username = Friends.username1)

```

You may have to fiddle with the SQL for your dialect - i think the above is ORacle SQL - but i might be wrong
So you are on exactly the right lines.

---

### Post by eviltang on 2008-10-28
> **mike_g said:**
> You could reduce redundancy and space usage by having the userfriends table simply storing a composite key linking users to friends. EG:
```

####USER####
uid      <-----+
username       |
email          |
password       |
               |
###FRIEND###   |
user_id -------+
friend_id -----+

```


Exactly.  I guess that I could not explain it very well.  This is my intent.  But the concept I guess that I cannot understand is if a person (uid) has multiple friends wouldnt it look like this:

username (user.uid) 1->many friends (friend.friend_id) many->many username (user.uid)?

again, I am not sure the best way to explain it.  joe being one uid would have many friends (1->many) many friends (friend_id) would have many *details* (uid) (many->many).

Is this the right way?  Would I just use queries based on the resulting array of friend_id's to populate the information (of the friends)?

Thanks again!

Please let me know if you need more clarification.

---

### Post by eviltang on 2008-10-28
> **Tony Flury said:**
> What you have is actually called a many to many - one user has many friends - and a user could be a friend to many other users.

The common way to model this in a relational database is to use a table which defines the relationships, so that each relationship in the database is one to many - relational databases don't handle Many to many well (without help).

Tables are therefore : 

User
username (Primary Key)
email

Friends
username1 
username2 

In the friends table both fields together form the primary key.

if you think about how this works - each entry in the User table will have many entries in the Friends table where they are username1, and also many where they are username2 - so you have got your many to many, but each row in Friends will only point to one User using username1 and one User using username2, which now means the queries are easy.

So this means it is not a million miles from what you suggested.

So the email adresses for all of "John"'s friends is 
```

Select u2.email From User as U2 WHERE (Friends.username1 = "John" and u2.username = Friends.username2) OR (Friends.username2 = "John" and u2.username = Friends.username1)

```

You may have to fiddle with the SQL for your dialect - i think the above is ORacle SQL - but i might be wrong
So you are on exactly the right lines.

Gotcha!  I get it.  I was worried about the "many to many" issue.  So my logic was just a little twisted on the second portion.  

I need to not think about it too hard.

Thanks!  (+thanks)

---

### Post by Tony Flury on 2008-10-28
if you think about the relationships between tables - that might help.

yes you have a many to many relationship between your users, but with that friends table in the picture it converts into two "one to many" relationships which are much nicer to deal with.

if you are happy we have solved your problem, you can mark the thread as solved, using the Thread Tools menu.

---

