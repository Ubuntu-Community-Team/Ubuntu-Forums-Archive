---
title: "[SOLVED] How do I get a value I just entered into a MySQL database with auto inc"
date: 2008-08-03
forum: Programming Talk
---

### Post by thenetduck on 2008-08-03
Hi What I mean is, 

I did a statment like

```

 "INSERT INTO projects (id,project_name) VALUES (NULL, "My Great Project"); 
```

now, I would like to know what the id value value (it's an auto inc) but am not sure an efficient way to do this? Is there a way to make a one statment that will return the id value as well as insert the project name? Thanks 

The Net duck

---

### Post by mssever on 2008-08-03
> **thenetduck said:**
> Hi What I mean is, 

I did a statment like

```

 "INSERT INTO projects (id,project_name) VALUES (NULL, "My Great Project"); 
```now, I would like to know what the id value value (it's an auto inc) but am not sure an efficient way to do this? Is there a way to make a one statment that will return the id value as well as insert the project name? Thanks 

The Net duck
You want the last insert id (which I think is a MySQL function). At any rate, consult the documentation for your MySQL bindings. You didn't mention what language you're using.

---

### Post by thenetduck on 2008-08-03
Sorry, 
I am using PHP / MySQL with PDO's Will that conflict with other users trying to access that database at the same time? or is it so quick that would never happen? 

Thanks 
The Net Duck

---

### Post by mssever on 2008-08-04
> **thenetduck said:**
> Sorry, 
I am using PHP / MySQL with PDO's Will that conflict with other users trying to access that database at the same time? or is it so quick that would never happen?
I'm not familiar with PDO, but many frameworks include the insert id in the object returned by the insert function. That should be safe to use, even with concurrent access. The raw PHP function (I no longer remember its name) may well be vulnerable to race conditions.

I suggest you read PDO's documentation for the definitive answer.

---

### Post by dwhitney67 on 2008-08-04
> **thenetduck said:**
> Hi What I mean is, 

I did a statment like

```

 "INSERT INTO projects (id,project_name) VALUES (NULL, "My Great Project"); 
```

now, I would like to know what the id value value (it's an auto inc) but am not sure an efficient way to do this? Is there a way to make a one statment that will return the id value as well as insert the project name? Thanks 

The Net duck
Since it appears that you are using MySQL, have you tried using LAST_INSERT_ID()?  This will return the last last used 'id' of your table.

---

### Post by drubin on 2008-08-04
use the php function
[PHP]mysql_insert_id();[/PHP]

Should return the last id inserted. Run that that after your query.

[PHP]
$q=mysql_query("INsert into blah blah blah");
$id= mysql_insert_id();
[/PHP]

---

### Post by cszikszoy on 2008-08-04
A general SQL way to do that would be:

```
SELECT id FROM projects ORDER BY id DESC
```

That would return a table of all of the id numbers in the projects table, sorted descending.  If you look at row 0, that will be the id number with the highest value, or the most recent (if it's an auto number).

Also, in your INSERT INTO statement, if the field is an auto number, you don't need to reference the field in your INSERT statement.

ie,
```
"INSERT INTO projects (id,project_name) VALUES (NULL, "My Great Project");
```

should be 

```
"INSERT INTO projects (project_name) VALUES ("My Great Project");
```

---

### Post by drubin on 2008-08-04
> **cszikszoy said:**
> A general SQL way to do that would be:

```
SELECT id FROM projects ORDER BY id DESC
```


This way will work if you ONLY have one user on your system. It is not a valid solution ever! in the real life. If you have 2 people viewing the website at the same time your id's will get mixed up.

Use the builtin function please :)

---

### Post by cszikszoy on 2008-08-04
> **rubinboy said:**
> This way will work if you ONLY have one user on your system. It is not a valid solution ever! in the real life. If you have 2 people viewing the website at the same time your id's will get mixed up.

Use the builtin function please :)

Unfortunately, the built in function does little more than what I wrote above.  Using the built in function does not protect you from updates to the database from multiple users.

This is taken from php.net's man pages:
```
**Note**:          Because **mysql_insert_id()** acts on the last performed     query, be sure to call **mysql_insert_id()** immediately      after the query that generates the value.    
```Other people on php.net's man page forum also claim that the built in function will only return the results from the last *query*, regardless if it was an update, insert or select.  

Further down the page (from **thomas at tgohome dot com**):
```

Be careful, because this operates on the last performed query, it includes UPDATEs and SELECTs as 'queries'. For example, this is what I set up.

INSERT post into database
UPDATE child forums with insert ID (insert ID is correct)
Insert ID = 0 because of last query
Send the user to their post - but fail because the insert ID is zero. 

So store it in a variable like $insert_id instead of querying it every time.

```


PHP.net's man page also suggests to use the SQL command LAST_INSERT_ID() instead.

More info here: [http://de3.php.net/mysql_insert_id](http://de3.php.net/mysql_insert_id)

---

### Post by drubin on 2008-08-04
> **cszikszoy said:**
> Unfortunately, the built in function does little more than what I wrote above.  Using the built in function does not protect you from updates to the database from multiple users.

That runs on the LAST query with the "current" connection, Different scripts would have different connection objects and therefore would not be included. 

When you run mysql_insert_id(); it is supposed to take in a connection resource, but if you do not include on the LAST connection resource that was created will be used.

This mysql_insert_id(); is safe with in the same php script, ie the same connection resource.

---

### Post by cszikszoy on 2008-08-04
> **rubinboy said:**
> That runs on the LAST query with the "current" connection, Different scripts would have different connection objects and therefore would not be included. 

When you run mysql_insert_id(); it is supposed to take in a connection resource, but if you do not include on the LAST connection resource that was created will be used.

This mysql_insert_id(); is safe with in the same php script, ie the same connection resource.

I wonder why people that posted on php.net's page had problems with it then?  I had never heard of the $mysql_insert_id() function until you mentioned it.  Also, did you note (on the page I linked to) that there would be problems with this if your auto increment field is a bigInt, instead of just an int?  Very curious.

---

### Post by drubin on 2008-08-04
> **cszikszoy said:**
> I wonder why people that posted on php.net's page had problems with it then?  I had never heard of the $mysql_insert_id() function until you mentioned it.  Also, did you note (on the page I linked to) that there would be problems with this if your auto increment field is a bigInt, instead of just an int?  Very curious.

> Caution

mysql_insert_id() converts the return type of the native MySQL C API function mysql_insert_id() to a type of long (named int in PHP). If your AUTO_INCREMENT column has a column type of BIGINT, the value returned by mysql_insert_id() will be incorrect. Instead, use the internal MySQL SQL function LAST_INSERT_ID() in an SQL query.


I think this might be because Mysql can handle up to 32bit numbers, where as mysql can handle 64 bits, I will look into this further, Thanks. :)

I use mysq_insert_id on sites that have a relatively big through put and have never had any issues.

---

### Post by cszikszoy on 2008-08-04
> **rubinboy said:**
> I think this might be because Mysql can handle up to 32bit numbers, where as mysql can handle 64 bits

You mean php can handle up to 32 bits, where mysql 64, right?

---

### Post by drubin on 2008-08-04
> **cszikszoy said:**
> You mean php can handle up to 32 bits, where mysql 64, right?

That is exactly what i meant, It has been a long long long day today. Think it is time to call it a day. :) Thanks for the correction

---

### Post by cszikszoy on 2008-08-04
We've all been there!  Enjoy your rest! :)

---

### Post by thenetduck on 2008-08-05
Thanks! This has been very helpful!. I am going to use a different PDO object for each class by encapslating my objects. This way I will have no issues. Thanks for all the help. 

The Net Duck

---

### Post by thenetduck on 2008-08-05
> **cszikszoy said:**
> A general SQL way to do that would be:

```
SELECT id FROM projects ORDER BY id DESC
```

That would return a table of all of the id numbers in the projects table, sorted descending.  If you look at row 0, that will be the id number with the highest value, or the most recent (if it's an auto number).

Also, in your INSERT INTO statement, if the field is an auto number, you don't need to reference the field in your INSERT statement.

ie,
```
"INSERT INTO projects (id,project_name) VALUES (NULL, "My Great Project");
```

should be 

```
"INSERT INTO projects (project_name) VALUES ("My Great Project");
```
thank you for this comment, It helped me later on with my PDO objects. .... 

this is the code that I am using to do everything works like a charm. 

```

 /*
      *  Summary: This function will be creating 
      *  a new proejct in the database, then making
      *  sure that that project is liked to the user.
      *  Process:
      *                 create a new database entry
      *                 link the database with the user
      */
     public function createNew($project_name)
     {
         // create a new project entry for projects
         $proj_stm = $this->conn->prepare("INSERT INTO projects (projects) VALUES(?)");
         $proj_stm->execute(array($project_name));
         // Gets the id that just got inserted into.
         $project_id = $this->conn->lastInsertID();
         // like user id up withe project id.
         $link_stm = $this->conn->prepare("INSERT INTO user_project_link (user_id, project_id) VALUES (?,?)");
         $link_stm->execute(array($_SESSION['logged_id'], $project_id));
     }

```

Thank you once again, 

The Net Duck

PDO Information ---- fell in love with PDO now I can't stop using em [http://us2.php.net/manual/en/book.pdo.php](http://us2.php.net/manual/en/book.pdo.php)

---

### Post by drubin on 2008-08-05
Glad it worked and got sorted, Mark it as solved.

---

