---
title: "joomla installation issue"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by charitosha on 2014-03-22
greeting everyone!
i am trying to install joomla but i run into an issue, i think that i messed up mysql installation but i'm not sure.
so before joomla i tried to install LAMP
apache2 works because i get the "IT WORKS!" message @ localhost
php works because @ [http://localhost/test.php](http://localhost/test.php) i get a page that describes the php version
now about mysql i run the following commands to verify if it's correctly installed:
cat etc/hosts | grep localhost
cat: etc/hosts: No such file or directory
cat /etc/mysql/my.cnf | grep bind-address
bind-address = 127.0.0.1
not sure why that file/directory doesn't exist

i went on trying to install joomla as i saw in the documantation, i got to the part where i should grand permisions to the database:
/var/www/joomla$ mysqladmin -u root -p create joomla
/var/www/joomla$ mysql -u root -p
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 47
Server version: 5.5.35-0ubuntu0.12.04.2 (Ubuntu)

mysql> GRAND SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON joomla.* TO 'joomla@localhost' IDENTIFIED BY 'password';

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'GRAND SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORA' at line 1

can anyone help/guide me getting through these problems that i got into??
if more info needed please ask me

---

### Post by PartisanEntity on 2014-03-22
> mysql> **_GRAND_** SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON joomla.* TO 'joomla@localhost' IDENTIFIED BY 'password';

Should be GRAN**_T_**

Try that.

---

### Post by josgeluk on 2014-03-22
Try "GRANT" instead of "GRAND".

---

### Post by charitosha on 2014-03-23
that's kinda embarrassing... didn't see that i wrote it wrong...
But i stubled upon another issue...
I am at the step where i modify joomla files, i found the file at var/www/joomla/[COLOR=#333333][FONT=Ubuntu]libraries/joomla/filter/input.php, but i couldn't find those 2 lines that i'm supposed to.
[/FONT][/COLOR]i found 2 similar lines: 
$source = preg_replace_callback('/&#(\d+);/m', "callbackJFilterInputConvertDecimal", $source);  
$source = preg_replace_callback('/&#x([a-f0-9]+);/mi', "callbackJFilterInputConvertHex", $source);  
those 2 are inside a protected function _decode($source), but before doing anything i want to be sure... as far as i can tell this file is up to date...
isn't it possible to do the modification via the terminal?
when i type sudo nano libraries/joomla/filter/input.php i get into the GNU nano. Isn't it possible to do the modification from there?

---

### Post by charitosha on 2014-03-25
can somebody help me getting throught the joomla instalation process? 
from [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) i'm at the step where i have to modify some joomla files...
i found the input.php file but,
it says that i have to find:
$source = preg_replace('/&#(\d+);/me', "utf8_encode(chr(\\1))", $source); 
[FONT=inherit][/FONT]$source = preg_replace('/&#x([a-f0-9]+);/mei', "utf8_encode(chr(0x\\1))", $source);but i couldn't find them anywhere in the particular file.
instead i found similar but not exact:
[COLOR=#000000]$source = preg_replace_callback('/&#(\d+);/m', "callbackJFilterInputConvertDecimal", $source); [/COLOR]
[COLOR=#000000]$source = preg_replace_callback('/&#x([a-f0-9]+);/mi', "callbackJFilterInputConvertHex", $source); [/COLOR]
what should i do? 
or is there another way to install joomla?

---

### Post by mastablasta on 2014-03-25
as far as i remember joomla you just run the install from a webbrowser and follow the prompts. 
[http://docs.joomla.org/J3.2:Installing_Joomla#tab=Requirements](http://docs.joomla.org/J3.2:Installing_Joomla#tab=Requirements)

i can't find your step in these instructions. and i don't remember doing those lines. i think they have something to do with the way character will be decoded. perhaps you the first two lines are not there maybe you could just add the second two lines.

also i used phpmyadmin to create the mysql databases.

i am thinking of switching my one joomla site to wordpress . as it really annoys me what i would need to do to "upgrade" which is essentially to create a new website and then move the data from old webpage. :-/

---

### Post by charitosha on 2014-03-25
the steps that i'm talking about are listed in: [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) ,where is says : Modify Joomla Files.
i'm almost done with the instalation as is recomended from help.ubuntu and don't want to install it other way now...
P.S. also can somebody explain me the following:
before going to install joomla i wanted to verify if apache2, php and mysql installed correctly...
now about mysql; i run the following commands to verify if it's correctly installed:
cat etc/hosts | grep localhost
cat: etc/hosts: No such file or directory
cat /etc/mysql/my.cnf | grep bind-address
bind-address = 127.0.0.1
not sure why that file/directory doesn't exist, is mysql installed correclty???
thanks in advance!

---

### Post by charitosha on 2014-03-25
ok ubuntu installed some updates regarging apache, php and the likes, rebooted and now i can see the joomla installation page! awesome!
anywayzZZZ one last question, because i don't know if it's going to affect me somehow in the future:
About mysql; i run the following commands to verify if it's correctly installed:
cat etc/hosts | grep localhost
cat: etc/hosts: No such file or directory
and
cat /etc/mysql/my.cnf | grep bind-address
bind-address = 127.0.0.1
not sure why that file/directory doesn't exist, is mysql installed correclty???
thanks in advance!
[B]!EDIT!

[/B]I am at the joomla installation proccess at step 4 Database. i get this ERROR: Could not connect to the database. Connector returned number: Unable to connect to the Database: Could not connect to MySQL.
why this have happened? how can i fix it? help pls

---

### Post by PartisanEntity on 2014-03-25
The first things to check, which are obvious but often overlooked, is that you entered the database user, database and password correctly.

The second thing that often causes issues is the hostname, here you usually enter "localhost".

---

### Post by Habitual on 2014-03-26
> **charitosha said:**
> 
cat etc/hosts | grep localhost
cat: etc/hosts: No such file or directory
don't use cat + grep. ;)
More efficient to use
```
grep localhost **[COLOR=#ff0000]/[/COLOR]**etc/hosts
```
> **]cat /etc/mysql/my.cnf | grep bind-address
bind-address = 127.0.0.1
not sure why that file/directory doesn't exist[/QUOTE]
and again:
```
grep "bind-address" /etc/mysql/my.cnf
```

[QUOTE=charitosha said:**
> 

```
mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON joomla.* TO 'joomla@localhost' IDENTIFIED BY 'password';
```

Testing your GRANT statement is a good step:

```
$ mysql -h 127.0.0.1 -u joomla -ppassword -e "show databases;" 
```or
```
$ mysql -h localhost -u joomla -ppassword -e "show databases;"
``` should work.

You should see the joomla db.
Have fun and Good Luck!

---

### Post by charitosha on 2014-03-26
ok so i have a very specific question:
i am at the joomla instalation proccess, at the 4th step where i have to configure databases.
all the time i get this error: ***Could not connect to the database. Connector returned number: Unable to connect to the Database: Could not connect to MySQL.***
in the terminal via the MySQL monitor i can see that i have created the database.
So why i get this error???

---

### Post by PartisanEntity on 2014-03-26
What database type are you selecting?

---

### Post by charitosha on 2014-03-26
MySQL (but i also tried MySQLi ) none worked

---

### Post by PartisanEntity on 2014-03-26
And you have tried both "localhost" and "127.0.0.1" for the hostname ?

---

### Post by charitosha on 2014-03-26
just tried 127.0.0.1 in both database types, still get : Could not connect to the database. Connector returned number: Unable to connect to the Database: Could not connect to MySQL.
why you think that this happens???

---

### Post by PartisanEntity on 2014-03-26
Have you tested that you can infact connect to mysql using the username and password you created?

In the terminal do the following:

```
mysql -h localhost -u username -p
```

replace "username" with the username you created for joomla. (In your case the username is "joomla")

After you hit enter, you should be prompted for a password, enter it and let us know if you succeeded.

---

### Post by charitosha on 2014-03-26
success. i entered my username it asked for my password and i'm the mysql monitor.
went back to the joomla page and it worked!!!:-k
			the only difference was that i also entered my password(it wasn't mandatory, that's why i didn't fill it in before)-don't know if that matters...
		
 	
thank you though!

---

### Post by PartisanEntity on 2014-03-26
Yes of course you need your password, that's what I asked you about earlier :)

Glad it worked :)

Please make sure to edit the title of this thread and add [solved] so that others can benefit.

---

