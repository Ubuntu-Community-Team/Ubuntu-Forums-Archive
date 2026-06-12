---
title: "[SOLVED] Why is MySQL not reconizing a string in my database?"
date: 2008-08-07
forum: Programming Talk
---

### Post by thenetduck on 2008-08-07
Hi

I have a database table named "projects" (you might recognized this table from a previous post, sorry) and it looks like this 

Table: projects
Col:   id, name 
sample: 1  Cool Project
        2  School Project


I am trying to extract the id from the name colum. I am using PDO's so it looks like this> 

(please note $this->conn is a PDO that I have created all ready that connect to my database correctly)

```

// $name is an incoming string "Cool Project";
$stm = $this->conn->prepare('SELECT id FROM projects WHERE name = ?'); 
$stm->execute(array($name));

// Get the id and return it in an array
$id = $stm->fetch();
echo $id[0];

```

This will echo nothing but should echo 1. I don't understand what I am doing wrong. Should'nt this work? I have tried taking "name = ?" and replacing it with "1 = 1" and this will echo 1 just fine. Can anyone see a reason this will  be messing up? 

Thanks for all the help,
The Net Duck

---

### Post by dwhitney67 on 2008-08-07
What is the question mark (?) for?

If you are trying to match a string that has a '?' in it, then I believe you need to encapsulate the question mark in quotes.
```
SELECT id FROM table WHERE name="?";
```
In your code, you may need to escape the double-quotes I used above.

---

### Post by drubin on 2008-08-07
> **thenetduck said:**
> This will echo nothing but should echo 1. I don't understand what I am doing wrong. Should'nt this work? I have tried taking "name = ?" and replacing it with "1 = 1" and this will echo 1 just fine. Can anyone see a reason this will  be messing up? 

Thanks for all the help,
The Net Duck

I am going to show you the most usefull php function in the whole world!!
[PHP]var_dump($var);[/PHP]

This "recursively" prints out all the details of a variable, if it is an array it  goes in to each element and does the same.

Please var_dump($id); (There is no need to echo var_dump, it already out puts it to the screen. See what the value of $id, you can see the type, and all the data it contains. :)

---

### Post by drubin on 2008-08-07
> **dwhitney67 said:**
> What is the question mark (?) for?

If you are trying to match a string that has a '?' in it, then I believe you need to encapsulate the question mark in quotes.
```
SELECT id FROM table WHERE name="?";
```

It is  a prepared statement. the query is prepared and replaces the ? for each time the query is run.

It is faster when you have the run the same query over and over again but with different data.

**EDIT:** but yes i think you do need to include the '?'  the $name is inserted in the place of the question mark and sql says strings need to be quoted. But sql uses single quotes.  '?'```
SELECT id FROM table WHERE name='?';
```

---

### Post by thenetduck on 2008-08-07
> **rubinboy said:**
> I am going to show you the most usefull php function in the whole world!!
[PHP]var_dump($var);[/PHP]

This "recursively" prints out all the details of a variable, if it is an array it  goes in to each element and does the same.

Please var_dump($id); (There is no need to echo var_dump, it already out puts it to the screen. See what the value of $id, you can see the type, and all the data it contains. :)

Thank you once again, again, will be using the var_dump() :) 

Looks like a trimming issue, man, I hate that. I spend like 2 hours last night trying to figure this out and the figured it out in 20 min the next day. ha. Thanks once again 

The Net Duck

---

