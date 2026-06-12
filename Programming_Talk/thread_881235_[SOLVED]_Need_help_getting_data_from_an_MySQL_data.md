---
title: "[SOLVED] Need help getting data from an MySQL database"
date: 2008-08-05
forum: Programming Talk
---

### Post by thenetduck on 2008-08-05
Hi I know I have been asking a lot of questions of late I just been having a lot of troubles wrapping my mind around MySQL etc. 

ok here is what I am trying to do. I have a database, and in the database I have three tables. "users": id, username, password  ---- "projects": id, projects ---- "user_project_link": user_id, project_id .

Ok so right now my table looks kind of like this: 

table:users
id   username   password
0    bob        bob
1    killer     killer


table:projects
id   projects
0    New great Project
1    another project
2    is three really nessary?.. project


table:user_project_link
user_id    project_id
1          0
1          1
0          2


What I am trying to do is display all of the the projects that "Bob" has created.Would the correct way to do this be something like this?

```

SELECT project_id FROM user_project_link WHERER user_id  = $bobs_id

```

Then just do something like 
```

SELECT projects FROM projects WHERE id = $what_i_got_from_the_other_statment 


```

Is there a simpler way to do this? Also, I am confused on how to user the information I get from my first select statement. 

Thanks 
The Net duck

---

### Post by grepgav on 2008-08-06
Use joining, ex:

SELECT projects FROM users u, projects p, users_projects_link up WHERE u.id = up.user_id AND up.project_id = p.id AND u.username LIKE 'bob';

That should work, although you would likely want to do the last part as a variable input. Also I would suggest that you should try and standardize the naming conventions for your database schema.

The 'id' column of each table should really have a unique name, and hopefully you are using them as a primary key which is generally auto-incramented and start at 1.

things like singular vs plural table names etc. start to get confusing if they are not consistant. I would reccomend something more like the following:

Table user:
user_id (primary key, auto_increment)
username
password

Table project:
project_id (primary key, auto_increment)
name

Table user_project:
user_project_id (primary key, auto_increment), -- This may seem excessive but always good to have a unique primary key for a table, and that value should have no inherent signifigance outside of being the PK for that table.
user_id -- (foreign key to user.user_id),
project_id  -- (foreign key to project,project_id)

Good luck!

---

### Post by dileepm on 2008-08-06
This goes easier

```
SELECT * FROM projects where projects.id in (SELECT project_id FROM user_project_link where user_id=0);
```

However there is a suggestion not to use the word "id" for any fields as they may conflict as reserved SQL keywords in programming languages...

---

### Post by cszikszoy on 2008-08-06
What you're trying to do can be achieved with the JOIN statement, as shown above.

But, your life will be much simpler if you design your tables correctly.  Remove the 3rd table, and simply add another field to the Projects table.  Call this field user_id, or whatever you want.  When you update or add a new project to the table, just include the user_id there.

This way, you can retrieve all projects owned by a user by using this SQL command:

```
SELECT * FROM projects WHERE user_id=<user_id>
```

Obviously, if this were some PHP variable (say, $user_id) you can just write:

```
SELECT * FROM projects WHERE user_id=$user_id
```

One of my favorite things about php is that it can parse variables inside the string, without needing to close the string, append some variable, then reopen the string.

---

### Post by dileepm on 2008-08-06
You need to optimize your table as storage and retrival process is critical for web applications.
You may have your tables this way

Table :users
user_id username password
0 bob bob
1 killer killer

Table :projects
project_id user_id projects
0          1       New great Project
1          1       another project
2          0       is three really nessary?.. project



[PHP]SELECT project_id,projects FROM projects where user_id=$user_id;[/PHP]

---

### Post by cszikszoy on 2008-08-06
> **dileepm said:**
> You need to optimize your table as storage and retrival process is critical for web applications.
You may have your tables this way

Table :users
user_id username password
0 bob bob
1 killer killer

Table :projects
project_id user_id projects
0          1       New great Project
1          1       another project
2          0       is three really nessary?.. project



[php]SELECT project_id,projects FROM projects where user_id=$user_id;[/php]

Beat you to it :)

---

### Post by pmasiar on 2008-08-06
> **cszikszoy said:**
> But, your life will be much simpler if you design your tables correctly.  Remove the 3rd table, and simply add another field to the Projects table.

But result would be not the same: old way, more than one user can be associated with the same project. Your way we lose that feature - so it depends what OP wants, but it is a beginner's mistake to assume that - you should have asked what is the goal, not to change design in an incompatible way.

Another beginner's mistake is to use SELECT *. In fact my old-school DB Admin had the rule: "If you have * in SELECT, you better have SELECT count(*), or else". But I am afraid that most PHP hackers do not know why... :-(

---

### Post by cszikszoy on 2008-08-06
> **pmasiar said:**
> But result would be not the same: old way, more than one user can be associated with the same project. Your way we lose that feature - so it depends what OP wants, but it is a beginner's mistake to assume that - you should have asked what is the goal, not to change design in an incompatible way.

Another beginner's mistake is to use SELECT *. In fact my old-school DB Admin had the rule: "If you have * in SELECT, you better have SELECT count(*), or else". But I am afraid that most PHP hackers do not know why... :-(

I suppose, but I would still be able to achieve the same functionality with only 2 tables.

If it were me, I would create another field in the users table.  Lets call it, associated_projects.  With a text data type, you can directly store the php array of the project_ids that the user belongs to.  Then, with this array, you can create a simple php loop (conveniently, with the foreach loop) to build your SQL string.

For example:

Let's say retrieving the projects associated with user_id 1 gave you an array such as this: [COLOR=#000000][COLOR=#0000bb]$projects [/COLOR][COLOR=#007700]= array([/COLOR][COLOR=#0000bb]1[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]2[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]3[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]4[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]5[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

Now, using this array, lets build or SQL statement.
```

[COLOR=#000000][COLOR=#0000bb]$sql [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]"SELECT * FROM projects WHERE "[/COLOR][COLOR=#007700];[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]$count [/COLOR][COLOR=#007700]=[/COLOR][/COLOR] [COLOR=#000000][COLOR=#0000bb]1;[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]foreach ([/COLOR][COLOR=#0000bb]$projects [/COLOR][COLOR=#007700]as [/COLOR][COLOR=#0000bb]$value[/COLOR][COLOR=#007700]) {
[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]   if ([/COLOR][COLOR=#0000bb]$count [/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]!=[/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb].sizeof($projects)[/COLOR][COLOR=#007700]) {
       [/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb]$sql [/COLOR][/COLOR][COLOR=#000000][COLOR=#007700].=[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000]"proj_id=[/COLOR][COLOR=#007700]$value[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000] OR "[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700];[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]
   } else {
    [/COLOR][/COLOR][COLOR=#000000][COLOR=#0000bb]$sql [/COLOR][/COLOR][COLOR=#000000][COLOR=#007700].=[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000]"proj_id=[/COLOR][COLOR=#007700]$value[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000]"[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700];[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]
   }[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]}[/COLOR][/COLOR]

```The result would be:

```

[COLOR=#000000][COLOR=#0000bb]$sql [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]"SELECT * FROM projects WHERE proj_id=1[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000] OR proj_id=2[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000] OR proj_id=3[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000] proj_id=4 OR [/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000]proj_id=5[/COLOR][/COLOR][COLOR=#000000][COLOR=#dd0000]"[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

```The if statement and the sizeof are required so that you don't print a trailing " OR " when you are building the SQL statement.

Furthermore, I couldn't really find anything supporting your claim that using SELECT * was incorrect.  In fact, nearly everything I found specificially uses SELECT *.

This website is great for information about anything SQL.  They even have a test section that will allow you to build your own queries and test it against their test DB table.

[http://www.w3schools.com/sql/](http://www.w3schools.com/sql/)

**forgot that string concat is .= in php, not +=

---

### Post by pmasiar on 2008-08-06
> **cszikszoy said:**
> I suppose, but I would still be able to achieve the same functionality with only 2 tables.

Not so.  You are completely missing idea of bridge tables to model many-to-many relations.

> that using SELECT * was incorrect. In fact, nearly everything I found specificially uses SELECT *.

It is bad practice. But you as PHP user are used to crappy code, so SELECT * is just normal I guess ... :-)

---

### Post by cszikszoy on 2008-08-06
> **pmasiar said:**
> Not so.  You are completely missing idea of bridge tables to model many-to-many relations.

I thought the idea was to associate multiple projects with any given user?

> **pmasiar said:**
> But result would be not the same: old way, more than one user can be associated with the same project. Your way we lose that feature


> **pmasiar said:**
> 
It is bad practice. But you as PHP user are used to crappy code, so SELECT * is just normal I guess ... :-)

Instead of insulting me, you could try to convince me (and, apparently, everyone else who uses PHP) why using select count(*) is better than select *.  I'm always willing to learn.

---

### Post by pmasiar on 2008-08-06
> **cszikszoy said:**
> I thought the idea was to associate multiple projects with any given user?

yes, but what if we need many users per given project, and many project per given user?

> why using select count(*) is better than select *.  

not related to PHP - just seems like people hacking PHP have higher tolerance to bad code. And i was right that some of them do not know why :-)

'SELECT *' is bad because:
- it pulls from DB all fields, not only those you need (wastes time and bandwidth)
- when you restructure DB, fields might be in different order and some queries (in hosting language, relying on field order) might break
- sure there are more... :-)

'SELECT count(*)' is completely different: it just counts rows (one number)

---

### Post by mssever on 2008-08-06
> **pmasiar said:**
> - sure there are more... :-)Indeed.

[LIST]
[*]Explicitly naming the columns you want makes your code easier to understand.
[*]Even if you're tempted to select * because you want all fields and don't care about order, remember that tables tend to gain fields over time (at least in my experience), and since your code doesn't know what to do with those new fields, it's wasteful to get them.
[/LIST]

---

### Post by drubin on 2008-08-06
> **dileepm said:**
> This goes easier

```
SELECT * FROM projects where projects.id in (SELECT project_id FROM user_project_link where user_id=0);
```

However there is a suggestion not to use the word "id" for any fields as they may conflict as reserved SQL keywords in programming languages...

Sub queries are very slow (relitivly) on larger tables

as for your conflict you can easierly solve these by encasing all your column names with ` back ticks, ie  `id` 

btw "id" is **not** a reserved word in mysql

---

### Post by drubin on 2008-08-06
> **pmasiar said:**
> 
'SELECT count(*)' is completely different: it just counts rows (one number)

It is faster to do a *count(1) FROM tablename ....* blah instead of using the *count(*)*,Just for speed reference.

---

### Post by thenetduck on 2008-08-06
Thank you for all the help. The reason I had three tables instead of two was because I was trying to follow proper data base normalization, however I can can see how having two databases could work for me two. 

I think I will stick with three tables however I am taking your advice to change the names to be consistant and easier to read. Thank you for the all the help, Makes my life easier

The Net Duck

---

### Post by pmasiar on 2008-08-06
Funny that the only 'thank' went to the guy who gave the **wrong** advice :-)

This shows how misleading the 'thanks' karma is. Seems than the more members in a mob, the studidier decisions are possible. I wonder how wikipedia copes with that. Possibly the only solution is egoless editing - to weed out the crap. Sadly, not possible here...

---

### Post by grepgav on 2008-08-07
I have to echo the comments above that in this situation you should def. have 3 tables. Unless you know for a fact that each and every project will only have one user assigned to it, and that will not ever change, it will be a Many-to-Many relationship and require that extra table.

Also you should try and avoid nested queries if possible because while the query optimization engine can make a joined statement more effecient, a nested query is harder to deal with and usually will result in worse performance, especially as the table size increases.

Even though id is not a reserved word it is still a better practice, in my opinion at least, to not use the same column name for every primary key because it gets uglier when you start dealing with foreign keys if you are trying to normalize the names of those.

---

### Post by thenetduck on 2008-08-07
> **pmasiar said:**
> Funny that the only 'thank' went to the guy who gave the **wrong** advice :-)

This shows how misleading the 'thanks' karma is. Seems than the more members in a mob, the studidier decisions are possible. I wonder how wikipedia copes with that. Possibly the only solution is egoless editing - to weed out the crap. Sadly, not possible here...

Hi.. I gave you a think star, no worries :) 

I appreciated your comment, so I think I actually ended up giving you two on accident. Anyway.. I usually give people thank stars that can help me. 

The Net Duck

---

