---
title: "MySQL connection problem..."
date: 2005-12-23
forum: Programming Talk
---

### Post by grim918 on 2005-12-23
im having a problem connecting to my mySQL database with php, here is my code:

//connect to server and select database
$conn = mysql_connect("server_name","user","password") or die(mysql_error());
mysql_select_db("db_name",$conn) or die(mysql_error());

when i run the script i get an error saying that the connection was lost. does anyone know if permissions also need to be set to connect to the mySQL server.

---

### Post by sapo on 2005-12-23
If you post the error it would be easier to help.

Btw, are you sure that your user, password, and database names are correct and that you HAVE that user and tables in your mysql database?

And of course, did you granted the permissions to that users to read/write on the database you are trying to connect?

---

### Post by grim918 on 2005-12-23
here is the error that i get:

Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /var/www/forums/do_addtopic.php on line 9
Lost connection to MySQL server during query

im pretty sure that the name of the user,password, and database are correct.
i think that i need to change the permissions to allow the user to write to the database but i dont know how to do that. i just switched from windows to linux and im still learning how to do basic things. do you know how i can change the permissions for the MySQL database.

---

