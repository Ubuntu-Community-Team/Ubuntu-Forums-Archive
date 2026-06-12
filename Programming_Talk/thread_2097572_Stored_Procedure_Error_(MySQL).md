---
title: "Stored Procedure Error (MySQL)"
date: 2012-12-23
forum: Programming Talk
---

### Post by kevinharper on 2012-12-23
```

SELECT COUNT(*), full_name, access_level
   FROM users
JOIN access_levels
   ON users.access_level_id=access_levels.id
WHERE users.active=1
AND username="admin"
AND password="pwd";
```
The above query returns the expected result.

I have created the following stored procedure
```

sp_authUser`(IN username VARCHAR(255), IN password VARCHAR(255), OUT full_name VARCHAR(255), OUT access_level VARCHAR(255))
BEGIN
SELECT users.full_name, access_levels.access_level
   FROM users
JOIN access_levels
   ON users.access_level_id=access_levels.id
WHERE users.active=1
AND users.username=username
AND users.password=password;

```
I have tried like 10 different queries and procedure declarations - even without any IN/OUT params. I keep getting the same error:
[COLOR="Red"]#1312 - PROCEDURE cis279JAVA.sp_authUser can't return a result set in the given context[/COLOR]

Here's how the procedure works:
I pass it 2 strings, username & password.
It returns 2 strings, full_name & access_level for any user who is active (users.active=1).

I don't think I can SSH to the server so I can't test whether I am getting this error because I am using phpMyAdmin. Anyone see what I'm doing wrong within the procedure?

I am executing it from an SQL window by:
```
CALL sp_authUser("admin", "pwd", @full_name, @access_level);
```

---

### Post by slickymaster on 2012-12-27
There is a reported bug in some versions of phpMyAdmin: 
[Bug #42548	PROCEDURE xxx can't return a result set in the given context]("https://bugs.php.net/bug.php?id=42548")

This behavior appears limited to SELECT statements within stored procedures inside phpMyAdmin.

Using a client like MySQL Workbench works around the problem, or you could upgrade phpMyAdmin, but that's a pain if you're on a shared server.

---

### Post by kevinharper on 2012-12-27
Yeah, I researched this quite a bit before posting the question, and ran into a lot of similar information.

I wish I could ssh to the db server so I could test it that way. I was kindda hoping someone would have found an error with what I was doing to set it or execute the procedure.

For the moment it looks like I will have to continue using a single DBQueries class.

---

### Post by slickymaster on 2012-12-28
Without knowing the way your database is designed and the structure of your tables in it, I would say that at a first glance there's no problems with your code.

---

### Post by kevinharper on 2012-12-28
I'm going to brave it and connect to these procedures from my Java program.

I'll revert to keeping my queries in a Java class if I can't get this to work over the weekend.

---

