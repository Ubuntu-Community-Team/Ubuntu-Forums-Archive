---
title: "How to enable sqlite3 with the php5.3?"
date: 2013-03-13
forum: Programming Talk
---

### Post by Newbie89 on 2013-03-13
I have look so many type of enable...but I still not very clear about on how to enable them...
Can  show me some clear step?Thanks...

---

### Post by greenpeace on 2013-03-13
Hey

Do you have sqlite library for php installed on your system?

```
sudo apt-get install php5-sqlite
```

Cheers,
Gp

---

### Post by Newbie89 on 2013-03-14
Ya...I already install...I want to know whether the version now support PDO only?

---

### Post by greenpeace on 2013-03-14
Hey, 

No, you can use the SQLite3 class to do it.

First, check that you've reloaded Apache after installing: 

```
sudo service apache2 reload 
```

Then you can test it with the following code, which you can put in /var/www/test-sqlite.php (or whatever you like) and then run it in your browser.
 
[PHP]<?php
  
  // open the db file (test.db) if it exists, or create it if it doesn't  
  $db = new SQLite3('test.db');
  
  // create a new table in the file
  $db->exec('CREATE TABLE test (id INT, message STRING)');
  
  // insert some things into it.
  $db->exec("INSERT INTO test (id, message) VALUES ('1', 'test message')");
  $db->exec("INSERT INTO test (id, message) VALUES ('2', 'test message 2')");
  
  // make a select
  $results = $db->query("SELECT * FROM test WHERE ID = 2");
                
  // print some results 
  print_r($results->fetchArray());
  
?>[/PHP]

Check your /var/www/apache2/error.log for errors, and check that apache has permissions to write to the directory where it will create the DB file.  This problem should be obvious from the logs.


Good luck,
Gp

---

