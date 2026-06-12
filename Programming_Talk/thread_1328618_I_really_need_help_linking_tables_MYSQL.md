---
title: "I really need help linking tables MYSQL"
date: 2009-11-16
forum: Programming Talk
---

### Post by joshdudeha on 2009-11-16
Hello everyone.

Basically, I am making a small site for my friends where we can create users and edit profiles and comment eachother.
Like a scaled down social network site. The problem is, I really can't get my head around the whole idea of relational databases.

What I have is a table for the users - which stores their username, password etc.
I then want this to link into my profile table, which stores their pictures and page-style information etc.
This could then link into other tables for things like comments or statuses etc.

I am using MySQL and I thought I could link e.g. the user table to the profile table by having the same id. For example, the user table has a user_id field (primary key) and a profile_id which links into the profile_id (primary key) on the profile table.
But I just don't get how to implement this.
It's really hard to explain. I want it, so that when a user registers - not only does the user_id auto increment, but so does the profile_id in the profiles table. And the pictures information and other information from the profile table can be used by the user table to define who the users are etc.

Could anyone please lend me a helping hand with this. I will try and explain more clearly if you would like.

Thank you a lot.

Josh

---

### Post by Can+~ on 2009-11-16
Databases are not things that you just pick up and use, there's a lot of theory behind it (see: Relational Algebra, Normalization, Indexing, Joining, between other things).

What you want is called a foreign key (that links the ID of one to the other), and probably add a trigger, function or stored procedure that splits/creates the registers between the two tables.

> I then want this to link into my profile table, which stores their pictures and page-style information etc.

That's a terrible idea, in fact, we had a user that had the same idea (storing raw html on a database). A database should store data that is relevant and retrieved quickly. 

Profile pictures and things should be stored as separate files, and possibly linked inside the database as references or hashing them (e.g username_userid_imageN.png, .css)

> Could anyone please lend me a helping hand with this. I will try and explain more clearly if you would like.

I don't want to be rude, but you're better off using something that already exists, either a framework or a site that lets you do this already (Google Groups?).

If you insist, I won't stop you, but you should probably start reading before continue asking.

---

### Post by mike_g on 2009-11-17
> I am using MySQL and I thought I could link e.g. the user table to the profile table by having the same id. For example, the user table has a user_id field (primary key) and a profile_id which links into the profile_id (primary key) on the profile table.
But I just don't get how to implement this.
For your user table set the id as auto increment. the MySQL code would be like:
```

CREATE TABLE user(
  id INTEGER AUTO_INCREMENT,
  ...
  PRIMARY KEY(id)
)
```
The profile table will then have a column refering to the user id (which is worth indexing). After inserting a user you can create insert a profile for the user using the last_insert_id.

> That's a terrible idea, in fact, we had a user that had the same idea (storing raw html on a database). A database should store data that is relevant and retrieved quickly.
Personally I would not store images and stuff inside the DB, but its not necessarily such a bad idea.

A commonly referenced user table with a 1-1 association with a less common but large profile table is a common SQL optimisation. The overhead of the join is offset by the speed increase gained by having less data in the commonly accessed table.

I also don't see much of an issue in storing raw HTML in a database, as long as its handled properly to avoid XSS.

---

### Post by joshdudeha on 2009-11-17
thanks a lot for your help. I have been trying to work this out dfor months.When you say about me storing files in the db. I didn't mean that, i will be storing the urls of those files in it.When im on my computer tonight. I will try and work it out again. Thanks again and ill get back (:

---

### Post by Tony Flury on 2009-11-17
If a user can have one and only one profile - then maybe you don't need a seperate table of profiles, and if you want to continue with a seperate table for other reasons then use the User_Id value as the Unique key into the profile table - that is completely allowed.

If a user can have more than one profile - maybe you are keeping a history of them - then I would use the User Id as a foriegn key in the Profile table - and (maybe) you would store the Profile_id value of the currently used profile in the User table - to save you having to search the profile table each time.

I would also councel against storing html/images in the database - I would have a module that extracts the data from the db and wraps it in html/css for display.

---

### Post by joshdudeha on 2009-11-17
I think I've worked out a way of doing it now. Like by using the user_id in the other table.
But thanks for your suggestions and help,it has helped me realise what I can do.

Cheers :D

---

### Post by Can+~ on 2009-11-17
Here's a basic idea of the layout (ASCII):

```

+--------------+
|     User     |
+--------------+
| id           |
| nickname     |
| username     |
| password     |
| age          |
| sex          |
| ...          |
+--------------+

+--------------+
|    Thread    |
+--------------+
| id           |
| title        |
| summary      |
| fk_author    | <-- foreing key to OP user
+--------------+

+--------------+
|   Comment    |
+--------------+
| id           |
| title        |
| content      |
| fk_thread    | <-- foreing key to the thread
| fk_author    | <-- foreing key to commenting user
+--------------+
```

```
User 1 -- * Thread 1 -- * Comment
```

(Very basic, didn't consider anything else, like avatars, proper naming of the ids, tagging, etc).

I'm not sure what's your reasoning behind segregating the "profile" and the "user", though.

---

### Post by joshdudeha on 2009-11-17
I guess I'm doing it because the user table just literally stores basic information such as password and username and name.
The profiles section will store everything from their information, picture urls, style information and just about everything else.
If I wanted them to have like photo albums, I could create a table which stores picture urls.

I just really need help with getting my head around foreign keys.
If I do what you did, Can+~ ; how would I go about doing it, because everytime I use foreign keys, nothing happens.

It's really confusing me. :(

---

### Post by akvino on 2009-11-17
> **joshdudeha said:**
> I guess I'm doing it because the user table just literally stores basic information such as password and username and name.
The profiles section will store everything from their information, picture urls, style information and just about everything else.
If I wanted them to have like photo albums, I could create a table which stores picture urls.

I just really need help with getting my head around foreign keys.
If I do what you did, Can+~ ; how would I go about doing it, because everytime I use foreign keys, nothing happens.

It's really confusing me. :(

If you are trying to link tables make sure you use InnoDB engine to create tables.

---

### Post by joshdudeha on 2009-11-17
Yeah I am using that, aha.
It's just confusing.

---

### Post by akvino on 2009-11-17
> **joshdudeha said:**
> Yeah I am using that, aha.
It's just confusing.

If you are using InnDB then you should be fine. Read what delete on cascade and update on cascade do. In essence you want to update on cascade and almost never delete on cascade. 

You will do well if you use integers for PK. 
I would put incremental integers (using these words since MYSQL, Oracle, MSSQL handle autoincrementals differently) as PK on every table. Then if you need to tie table just kreate a field called tablename_fk, and you are set.

---

