---
title: "PHP: Values inserted in wrong table"
date: 2012-12-30
forum: Programming Talk
---

### Post by sid0972 on 2012-12-30
hey

i want to insert values in a table in a database and somehow end up inserting values in a table which i dont know where is (its really confusing)

this is my code to insert values 

[PHP]
function about_me_insert($aname,$location,$occupation,$username)
{
    $conn=db_connect();
 $result=$conn->query("update users set user_aname='".$aname."', user_location='".$location."', user_occupation='".$occupation."' where username='".$username."' ");
 
 if(!$result)
 {
     echo "couldnt do it, sorry!!";
 }

    if ($result->num_rows>0) {
    throw new Exception('Duplicate Details.');
  }
else{
echo "Details saved with following parameters",$aname,$location,$occupation;}
}
[/PHP]and this is the output of the ```
select * from table 
``` query

```
mysql> select * from users;
+---------+----------+------------------------------------------+---------------------+-----------+----------------+--------------------+------------+-----------------------+-------------+---------------+--------------+-----------------+------------+
| user_id | username | user_pass                                | user_email          | user_bday | user_lastvisit | user_login_attemps | user_posts | user_allow_viewonline | user_avatar | user_location | user_newpass | user_occupation | user_aname |
+---------+----------+------------------------------------------+---------------------+-----------+----------------+--------------------+------------+-----------------------+-------------+---------------+--------------+-----------------+------------+
|       5 | sid      | b1b3773a05c0ed0176787a4f1574ff0075f7521e | abcde@yahoo.co.in | NULL      |           NULL |               NULL |          0 |                  NULL | NULL        | home          | NULL         | NULL            | NULL       |
+---------+----------+------------------------------------------+---------------------+-----------+----------------+--------------------+------------+-----------------------+-------------+---------------+--------------+-----------------+------------+
1 row in set (0.00 sec)

```it says it inserts value in the tables, but it actually does something else, cause the output of that is empty

and that 'home' in user_location is inserted by me **through** mysql itself

---

### Post by slavik on 2012-12-30
did you try turning on autocommit or committing the changes from php code?

side note: SQL injection much?

---

### Post by sid0972 on 2012-12-30
no i didnt commit the changes from php,  how that can be done?
also,how do i turn on autocommit?

this is running on my local machine, so i dont think SOL injection might be the cause

but this commit thing might be

---

### Post by slavik on 2012-12-30
google will help in either case ...

[http://us3.php.net/manual/en/pdo.commit.php](http://us3.php.net/manual/en/pdo.commit.php)

---

### Post by CodyPy1 on 2012-12-31
Icky, I'd go through a few more php/mysql tutorials if i were you.

---

### Post by sid0972 on 2012-12-31
which i am doing
btw is there anything wrong with my code??

---

### Post by kevinharper on 2013-01-01
I took a quick glance, it doesn't look like it.

As a suggestion though, maybe you could pull out the sql.
```

$sql = "UPDATE users
           SET user_aname='".$aname."', user_location='".$location."', user_occupation='".$occupation."'
        WHERE username='".$username."'";

$result=$conn->query($sql);
```
Helps me more easily debug queries.
(I did not change your query. There may be errors in it.)

---

### Post by sid0972 on 2013-01-01
ok,i'll try this way also

---

