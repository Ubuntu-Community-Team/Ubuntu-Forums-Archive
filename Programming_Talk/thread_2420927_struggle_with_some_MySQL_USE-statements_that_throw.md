---
title: "struggle with some MySQL USE-statements that throw back errors all the time:"
date: 2019-06-13
forum: Programming Talk
---

### Post by dilbert_one on 2019-06-13
Hello dear all - good day dear ubuntu-experts,


first of all - i am still wondering if this is the best place to put this question to. Since this is also a server-issue i guess that this "programming-"superforum is one of the best plcaces ever to ask this  qustion,
well i struggle with some MySQLstatements that throw back errors all the time. Hope you can help me here.

```

SHOW GRANTS FOR CURRENT_USER;

```




i have tried out various things in order to run this statement correctly 

```
USE jo ;
SHOW GRANTS FOR CURRENT_USER;

```

```
USE jo ;
SHOW GLOBAL VARIABLES LIKE 'PORT';


```
[h=3]Failed to execute SQL : SQL USE jo; SHOW GRANTS FOR CURRENT_USER; failed : You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'jo; SHOW GRANTS FOR CURRENT_USER' at line 1[/h]
**note**: my db-name; jo 


**see what i i  get back: **


```
Failed to execute SQL : SQL USE jo; SHOW GRANTS FOR CURRENT_USER; failed : You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'jo; SHOW GRANTS FOR CURRENT_USER' at line 1
```


**the question is**: do i need any quotations here to run the SQL-Startement. According to the manual i do not have to do that.. 


see the manual: [https://beginner-sql-tutorial.com/sql-use-database.htm](https://beginner-sql-tutorial.com/sql-use-database.htm)


USE yourdatabase;
SHOW GRANTS FOR CURRENT_USER;
> 

SQL USE Statement
The USE Statement is used to select a database and perform SQL operations into that database.
The database remains default until end of session or execution of another USE statement with some other database.
SQL USE DATABASE Statement: 
The Syntax for the USE Statement is:
USE database_name;
database_name - is the name of the database to be selected





Background:  during the installation of wordpress on a rootserver where i can configure and administer via webmin 
i get the feedback: Error establishing a database connection




i have gathered some more infos and insights due to some more tests.


see the following data: &#8211; the outcome of a testscript which i have put on the server

> 
Warning: mysqli_connect(): (HY000/2002): No such file or directory in /sites/www.mysite.de/tests.php on line 3
Warning: mysqli_error() expects parameter 1 to be mysqli, boolean given in /sites/www.mysite.de/tests.php on line 4
could not connect:
 


see the script: 


**on a sidenote,. &#8230;**


```
<?ph
if(function_expists('mysqli_connect')){
if(!($link = mysqli_connect('localhost','user','passwd','my_db'))){
die('could not connect: ' . mysqli_error($link));
}
} else {
die("don't have mysqli");
}
echo 'connect successfully';
mysqli_close($link);

```

well i guess that this is saying that 1 parameter was required, 0 were provided. and besides this we surely can say that there absolutly no error checking is being done before calling the function, it&#8217;s blindly passing a variable that was collected.
interesting: This actually makes sense, given i am probably failing to connect to mysql. What we don&#8217;t see is validation that the credentials work, & i can connect. one option would be to ssh to the php server, & then connect over the cli to mysql. Otherwise, we´re just guessing. Above all &#8211; we can say that there probably is no pathing issue. honestly &#8211; there are serious doubts that wordpress has a pathing issue, or this is anyway code related.



**background**: i have gotten the Error establishing a database connection


> This either means that the username and password information in your wp-config.php file is incorrect or we can&#8217;t contact the database server at localhost. This could mean your host&#8217;s database server is down.
Are you sure you have the correct username and password?
Are you sure that you have typed the correct hostname?
Are you sure that the database server is running?
If you&#8217;re unsure what these terms mean you should probably contact your host. If you still need help you can always visit the WordPress Support Forums.


guess that i have to edit all the stuff manually now.. 


i want to edit the file now and i will afterwards store it as wp_config.php on the server ab.  
Btw: i am still wondering why this was not happening  so far


additionally &#8211; i will do the following 


> First thing you should do is to make sure that you are getting the same error on both the front-end of the site, and the back-end of the site (wp-admin). If the error message is the same on both pages &#8220;Error establishing a database connection&#8221;, then proceed onto the next step. If you are getting a different error on the wp-admin for instance something like &#8220;One or more database tables are unavailable. The database may need to be repaired&#8221;, then you need to repair your database.


gem. [https://www.wpbeginner.com/wp-tutorials/how-to-fix-the-error-establishing-a-database-connection-in-wordpress/](https://www.wpbeginner.com/wp-tutorials/how-to-fix-the-error-establishing-a-database-connection-in-wordpress/)


Well at the moment i do not know how to proceed.. 


Love to hear from you

---

