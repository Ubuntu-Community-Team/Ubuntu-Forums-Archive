---
title: "sqlite3"
date: 2007-04-16
forum: Programming Talk
---

### Post by LaRoza on 2007-04-16
I downloaded sqlite, for Linux and Windows and I have a few questions.

I can create and query databases with it, but how do I connect to it with Python and PHP?

---

### Post by LaRoza on 2007-04-17
I received no responses to this and instead of asking again, I replied to it to make the question seem more interesting. Perhaps I should have titled the post "Python and SQLite" to pique more interest.

---

### Post by pmasiar on 2007-04-17
1) You are right - mentioning Python in title would make me to peek in :-)

2) quick Google search gives [pysqlite](http://www.initd.org/tracker/pysqlite) and  [devshed article](http://www.devshed.com/c/a/Python/Using-SQLite-in-Python/), and also [official docs](http://docs.python.org/lib/module-sqlite3.html). Something does not work as advertised? Any bugs/error messages in your test code?

Or are you having problems reading some obsure words? :-)

3) To use it from code, connect to database and execute query. SELECT query returns data access object, you cal loop through, docs shows how - not sure what is the source of your confusion. What are you trying to do?

---

### Post by LaRoza on 2007-04-17
I am in school using their Internet. I did not have any access to any online tutorials over the break. I just did not know how to connect because I did not have anything but the app (.bin and .exe) at home and had to figure things out for myself. 

Thanks for the links and help.

Next time I want a rapid response I may just write "Microsoft is better than Linux, VBScript rules - Python drools, buy - don't share..."

Imagine the amount of views I would get.:D

---

### Post by mrsticks on 2008-01-22
I have had good success with PHP's PDO.  It's an object orientated way of getting data from databases.  I have not used it extensively, I am also just starting to look into sqlite3.

[http://us.php.net/pdo](http://us.php.net/pdo)

Some example code:
```

<?php
       $dbh = new PDO("sqlite:/var/www/sqlite/database.sdb");

        $sql = "SELECT * FROM Inventory;";

        $results = $dbh->query($sql);

        foreach($results as $data) {
                echo {$data["ModelDescription"]."<br>";
                echo {$data["SerialNumber"]."<br>";
                echo $data["AssignedUser"]."<br>";
                echo $data["AssignedProgram"]."<br>";
        }
?>

```

HTH

-peter

---

### Post by stevescripts on 2008-01-22
LaRoza,

Just a quick note.

*If* tcl/tk is an option that interests you, the precompiled binaries are at:
     [http://www.sqlite.org/download.html](http://www.sqlite.org/download.html)

(same link as the sqlite3 binaries)

One of the most important features (for me) is the database compatability
between linux and windows.

Just in case some folks aren't aware of it, SQLite now supports Full Text Search ;)

Steve

---

