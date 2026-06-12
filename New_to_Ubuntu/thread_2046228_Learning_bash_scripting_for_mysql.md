---
title: "Learning bash scripting for mysql"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2012-08-22
Hi guys

I've recently begun learning bash scripting and I'd like to be able to scrip creating mysql databases.

Does anyone have any good material to help me with this. I've been unable to get it to work so far.

I want to take input for username, password, databasename and then create a new user with the given password, then create the database with the given name and grant the given user all privleges on the new database.

As soon as I get chance to test it again to c&p the output I'll post my code and output but for now any good guides, tips, coding samples you could point me to would be much appreciated.

---

### Post by bigmonmulgrew on 2012-08-22
OK heres my code

This is what I've found so far by googling
```
#!/bin/bash

###Variables
username="user1"
password="user1"

databasename="database1"

sudo mysql -u rootuser -prootpassword mysql -e "CREATE DATABASE $databasename; GRANT ALL PRIVILEGES ON  $databasename.* TO $username@localhost IDENTIFIED BY $password; FLUSH PRIVILEGES;"
```


Any ideas where I'm going wrong.
I don't get any error messages when I run the script but it seems to do nothing.

---

### Post by mapes12 on 2012-08-22
Just curious, but why the need to script mysql management when phpMyAdmin is out there?

---

### Post by bigmonmulgrew on 2012-08-23
mostly academic really although the  script ive written does a lot more than create  a mysql database. I just simplifies it her because this is the bit i cant get to work.

---

### Post by Azdour on 2012-08-23
Hi,

I would break your script into pieces to see what's failing, also you do not need to use sudo with the mysql command:

```

mysql -u rootuser -prootpassword -e "CREATE DATABASE $databasename;"

mysql -u rootuser -prootpassword -e "GRANT ALL PRIVILEGES ON  $databasename.* TO $username@localhost IDENTIFIED BY $password; FLUSH PRIVILEGES;"

```

Also is user1 already a user in MySQL?

---

### Post by Lisiano on 2012-08-23
To get input from the user, you can use read
```

#!/bin/bash
#Defaults
username="user1"
password="user1"
database="database1"
#Get variables from the user
read -e -p "Username: " -i $username username
read -e -s -p "Password: " -i $password password; echo
read -e -p "Database name: " -i $database database

echo "You are $username and you have $password for a password. You also have $database as a database"

```
```
lisiano@Lisiano-Ubuntu:/run/shm$ bash test.sh 
Username: Lisiano
Password:
Database name: Megadatabase
You are Lisiano and you have Secretpass for a password. You also have Megadatabase as a database
lisiano@Lisiano-Ubuntu:/run/shm$ 
```
-e - Use readline to get input
-s - Silent, AKA don't echo the output.
-p - Set a prompt for a user
-i - Preenter a value
username/password/database - The last argument is the variable to which the input will be assigned to.

EDIT: To read more about read and other bash commands, use this
```
man builtins
```

---

### Post by bigmonmulgrew on 2012-08-29
> **Lisiano said:**
> To get input from the user, you can use read
```

#!/bin/bash
#Defaults
username="user1"
password="user1"
database="database1"
#Get variables from the user
read -e -p "Username: " -i $username username
read -e -s -p "Password: " -i $password password; echo
read -e -p "Database name: " -i $database database

echo "You are $username and you have $password for a password. You also have $database as a database"

```
```
lisiano@Lisiano-Ubuntu:/run/shm$ bash test.sh 
Username: Lisiano
Password:
Database name: Megadatabase
You are Lisiano and you have Secretpass for a password. You also have Megadatabase as a database
lisiano@Lisiano-Ubuntu:/run/shm$ 
```
-e - Use readline to get input
-s - Silent, AKA don't echo the output.
-p - Set a prompt for a user
-i - Preenter a value
username/password/database - The last argument is the variable to which the input will be assigned to.

EDIT: To read more about read and other bash commands, use this
```
man builtins
```

Thanks for that I was using 'read' but your solution is more elegant than mine. I just simplified it here to concentrate on the SQL part.

---

### Post by bigmonmulgrew on 2012-08-29
> **Azdour said:**
> Hi,

I would break your script into pieces to see what's failing, also you do not need to use sudo with the mysql command:

```

mysql -u rootuser -prootpassword -e "CREATE DATABASE $databasename;"

mysql -u rootuser -prootpassword -e "GRANT ALL PRIVILEGES ON  $databasename.* TO $username@localhost IDENTIFIED BY $password; FLUSH PRIVILEGES;"

```

Also is user1 already a user in MySQL?

Ok I have split it as you suggested
I'm still seeing nothing

user1 does not exist, I was under the impression for the samples I found that the above command would also create user1. Is this not correct

---

### Post by Azdour on 2012-08-29
Hi,

It's strange you are not seeing any error messages.

Anyway there is nothing in what you have posted that creates user1, so you need to do this, off the top of my head.

```

mysql -u rootuser -prootpassword -e -e "create USER '$username'@'localhost' IDENTIFIED BY '$password'"

```

---

### Post by bigmonmulgrew on 2012-10-30
Right I gave up on this for a while as I was plannign on upgrading to ubuntu 12.04 LTS and though it best to test it there.

Still getting the same problem but after some experimenting I have found its the . in a database name that it does not like.

This works

```
#!/bin/bash                                                                                                                                                                                                                                                                   
domainname=testcouk                                                                                                                                                                                                                                                         
username="testuser"                                                                                                                                                                                                                                                          
password="testuser"                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                              
mysql -u root -ppassword mysql -e "CREATE USER '$username'@'localhost' IDENTIFIED BY  '$password';"                                                                                                                                                                          
mysql -u root -ppassword mysql -e "CREATE DATABASE $domainname;"                                                                                                                                                                                                             
mysql -u root -ppassword mysql -e "GRANT ALL PRIVILEGES ON  $domainname.* TO $username@localhost;"    
```

but this does not

```
#!/bin/bash                                                                                                                                                                                                                                                                   
domainname=test.co.uk                                                                                                                                                                                                                                                         
username="testuser2"                                                                                                                                                                                                                                                          
password="testuser2"                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                              
mysql -u root -ppassword mysql -e "CREATE USER '$username'@'localhost' IDENTIFIED BY  '$password';"                                                                                                                                                                          
mysql -u root -ppassword mysql -e "CREATE DATABASE $domainname;"                                                                                                                                                                                                             
mysql -u root -ppassword mysql -e "GRANT ALL PRIVILEGES ON  $domainname.* TO $username@localhost;"    
```

I don't see what it has against the . as I can create the database with this name using phpmyadmin. 
Any ideas

---

### Post by Azdour on 2012-10-31
Hi,

I think your problem may lie in the dots in the domainname in the second example, have you tried:

```
'$domainname'.*
```

---

### Post by bigmonmulgrew on 2012-10-31
> **Azdour said:**
> Hi,

I think your problem may lie in the dots in the domainname in the second example, have you tried:

```
'$domainname'.*
```

Yes I have tried that I get the following errors

```
ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''test.co.uk'' at line 1                                                                                  
ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''test.co.uk'.* TO testuser2@localhost' at line 1  
```

---

### Post by Azdour on 2012-10-31
Hi,

Looking at:

[http://dev.mysql.com/doc/refman/5.1/en/grant.html](http://dev.mysql.com/doc/refman/5.1/en/grant.html)

It does not include any examples where the database or table name used for the privilege level contains dots.

Is $domainname your database or a table?

---

### Post by bigmonmulgrew on 2012-10-31
> **Azdour said:**
> Hi,

Looking at:

[http://dev.mysql.com/doc/refman/5.1/en/grant.html](http://dev.mysql.com/doc/refman/5.1/en/grant.html)

It does not include any examples where the database or table name used for the privilege level contains dots.

Is $domainname your database or a table?

its a database. There must be a way to do it because phpmyadmin seems to do it fine

Basically it should go
Create user
Create database
grant user all priv on database

---

### Post by Azdour on 2012-10-31
Hi,

I'm running out of ideas, how about using backticks: `$domainname`?

---

### Post by bigmonmulgrew on 2012-10-31
> **Azdour said:**
> Hi,

I'm running out of ideas, how about using backticks: `$domainname`?

That does work when doing things directly at the command line but when running it from the bash script I get the following error

```
/home/admindm/bin/create.sql: line 7: test.co.uk: command not found                                                                                                                                                                                                           
ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1                                                                                              
/home/admindm/bin/create.sql: line 8: test.co.uk: command not found                                                                                                                                                                                                           
ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '* TO testuser2@localhost' at line 1    
```

---

### Post by Azdour on 2012-10-31
Hi,

Can you post you script again that uses the backticks. It's just that the error messages seem to be complaining about the ' single quote character.

---

### Post by bigmonmulgrew on 2012-10-31
heres the script with backticks

```
#!/bin/bash                                                                                                                                                                                                                                                                   
domainname=test.co.uk                                                                                                                                                                                                                                                         
username="testuser2"                                                                                                                                                                                                                                                          
password="testuser2"                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                              
mysql -u root -ppassword mysql -e "CREATE USER '$username'@'localhost' IDENTIFIED BY  '$password';"                                                                                                                                                                          
mysql -u root -ppassword mysql -e "CREATE DATABASE `$domainname`;"                                                                                                                                                                                                           
mysql -u root -ppassword mysql -e "GRANT ALL PRIVILEGES ON  `$domainname`.* TO $username@localhost;"                                                                                                                                                                         
                                                                                                       
```

I've also tried it like this putting the backticks inside the variable

```
#!/bin/bash                                                                                                                                                                                                                                                                   
domainname=`test.co.uk`                                                                                                                                                                                                                                                         
username="testuser2"                                                                                                                                                                                                                                                          
password="testuser2"                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                              
mysql -u root -ppassword mysql -e "CREATE USER '$username'@'localhost' IDENTIFIED BY  '$password';"                                                                                                                                                                          
mysql -u root -ppassword mysql -e "CREATE DATABASE $domainname;"                                                                                                                                                                                                           
mysql -u root -ppassword mysql -e "GRANT ALL PRIVILEGES ON  $domainname.* TO $username@localhost;"                                                                                                                                                                         
                                                                                                       
```

---

### Post by Azdour on 2012-10-31
Hi,

Ok, I think I may have it:

```
\`$domainname\`.*
```

I think it's the " quotes causing the problem. You need the \ character to escape the ` backticks. That worked for me when I tried it via command line.

---

### Post by bigmonmulgrew on 2012-10-31
EUREKA!!!

I found how to do it.
The variable does need to be enclosed in backticks so that MYSQL ignores the . but bash considers a backtick to be a special character. To make it work i had to use a backslash before each backtick to tell bash to ignore it as follows

```
#!/bin/bash                                                                                                                                                                                                                                                                   
domainname=test.co.uk                                                                                                                                                                                                                                                         
username="testuser2"                                                                                                                                                                                                                                                          
password="testuser2"                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                              
mysql -u root -ppassword mysql -e "CREATE USER '$username'@'localhost' IDENTIFIED BY  '$password';"                                                                                                                                                                          
mysql -u root -ppassword mysql -e "CREATE DATABASE \`$domainname\`;"                                                                                                                                                                                                         
mysql -u root -ppassword mysql -e "GRANT ALL PRIVILEGES ON  \`$domainname\`.* TO $username@localhost WITH GRANT OPTION;"                                                                                                                                                     
                                                                                                                           
```

---

### Post by bigmonmulgrew on 2012-10-31
Hi thanks for your help, just realised what was happening myself and googled bash special characters

---

