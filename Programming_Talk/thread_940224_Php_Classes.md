---
title: "Php Classes"
date: 2008-10-06
forum: Programming Talk
---

### Post by Dr Small on 2008-10-06
I am trying to grasp the concept of classes with Php, while attempting to write my own to begin with. I am trying to create a class to connect to a MySQL database, and run a query, like as follows:

```
<?php

class DB {

        function connect() {
                $this->connection = mysql_connect('localhost', 'drsmall', 'password');


                mysql_select('linuxblogs', $this->connection)
                or die(mysql_error());
                }

        function query($id) {
                mysql_query($id,$this->connection)
                or die(mysql_error());
                }
}

?>

```

So then, on another page, I would have:
```
<?php
require_once "class.php";
$db = new DB();

echo mysql_result($db->query("SELECT value FROM settings WHERE id='sitename'"),0);

?>
```

But, the problem is, I am receiving an error on line 14 of class.php, which is this:
```
mysql_query($id,$this->connection)
```
And the error states:
```
Warning: mysql_query(): supplied argument is not a valid MySQL-Link resource
```

It seems to me, that query() is not reading $this->connection. Like I said, I'm just beginning at this, so any help would be appreciated to where I have messed up.

Dr Small

---

### Post by drubin on 2008-10-06
> **Dr Small said:**
> 
```
<?php
class DB {
        **var connection;**
        function connect() {
                $this->connection = mysql_connect('localhost', 'drsmall', 'password');


                mysql_select('linuxblogs', $this->connection)
                or die(mysql_error());
                }

        function query($id) {
//you need to return the result back else no one is going to know you even queried the db. :) 
                **return**  mysql_query($id,$this->connection)
                or die(mysql_error());
                }
}

?>

```

So then, on another page, I would have:
```
<?php
require_once "class.php";
$db = new DB();
**$db->connect();**  //You need to be connected to the data base before querying it.
echo mysql_result($db->query("SELECT value FROM settings WHERE id='sitename'"),0);

?>
```


I am not sure if my comments will show up, but hopfully they will be bold.. I tried to point out where you are going wrong. Let me know if you need more details.(this i the last post before bed)

---

### Post by Dr Small on 2008-10-06
Thanks for those tid-bits of help. It really was helpful, although it wasn't exactly working, but I still got it to work in the end, through your advice.

For query(), I did this:
```
function query($id) {
$value = mysql_query($id,$this->connection);
return $value;
}
```

And that seemed to have solved the problem. Now I can begin tackling bigger projects and rewriting the MySQL to use Classes. Thanks Ruinboy!!

---

### Post by drubin on 2008-10-07
You may want to take a look at this
[http://www.php.net/manual/en/class.mysqli.php](http://www.php.net/manual/en/class.mysqli.php)

---

### Post by deuce868 on 2008-10-07
If you don't have any really heavy speed requirements, also check out some of the existing DB libraries. I like Doctrine, [http://www.doctrine-project.org/](http://www.doctrine-project.org/)

but it can be a bit slow if you do a ton of data loading and such. The API and such is very nice though.

---

### Post by drubin on 2008-10-07
> **deuce868 said:**
> If you don't have any really heavy speed requirements, also check out some of the existing DB libraries. I like Doctrine, [http://www.doctrine-project.org/](http://www.doctrine-project.org/)

but it can be a bit slow if you do a ton of data loading and such. The API and such is very nice though.

Also pear have a nice DB class.. (alot slower then raw code but for single server nice platform to start off with)

But then again creating your own one is a learning experience!!! and teaches you alot more then what you will get from using a pre existing class

---

### Post by skotos on 2008-10-07
Probably writing a class to manage database queries as a first try might take you far away from success, because the connection to the database is a particular case that is best faced using probably the simplest design pattern known as singleton (but these are advanced topics) to avoid creation of multiple, not useful and possibly overwhelming database connections.
Thus, I would suggest you to start writing a class for something you have to store into the database and then storing it thru a mysqli class instance you can directly derive / copy from the php site where many good samples can be found for any experience level.

Using a mysqli instance, in fact, might help you better understand how objects can be used and then, thru this experience, learn without hassles the right direction to follow.

As a developing platform for php I would suggest you Eclipse PDT all-in-one that works out of the box and provides easy hints, highlights and links to your functions, classes and many more helping tools for beginners and advanced programmers as well.
Just to look at the surface go and see this short youtube tutorial: [http://www.youtube.com/watch?v=VRFZpk-YHl4](http://www.youtube.com/watch?v=VRFZpk-YHl4)

---

### Post by drubin on 2008-10-07
> **skotos said:**
> As a developing platform for php I would suggest you Eclipse PDT all-in-one that works out of the box and provides easy hints, highlights and links to your functions, classes and many more helping tools for beginners and advanced programmers as well.
Just to look at the surface go and see this short youtube tutorial: [http://www.youtube.com/watch?v=VRFZpk-YHl4](http://www.youtube.com/watch?v=VRFZpk-YHl4)

Huge +1

---

