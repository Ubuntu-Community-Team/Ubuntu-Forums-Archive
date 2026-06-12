---
title: "automatic entry of password in bash script"
date: 2012-07-20
forum: Programming Talk
---

### Post by fivestaar on 2012-07-20
hi all

I have written a bash script to extract data from multiple tables and create a xml file for each of the tables.

```

#! /bin/bash

mysql -uroot -p --xml -e'SELECT * FROM handwriting.trial'>/home/divya/Desktop/trialData.xml
ssh-keygen;
mysql -uroot -p --xml -e'SELECT * FROM handwriting.words'>/home/divya/Desktop/wordsData.xml
mysql -uroot -p --xml -e'SELECT * FROM handwriting.writers'>/home/divya/Desktop/writersData.xml



```

Every time the program connects with mysql, it asks for the password which ruins the whole purpose of writing a script to make the whole process automated.

is there any way i can make the entry of password automated as well?

Both, the database and the script is run on the same computer, there is no need to connect to another computer.

---

### Post by sudodus on 2012-07-20
.

---

### Post by richpri on 2012-07-20
Try this:
Group all the select statements into a file ie: scriptfile.txt
then execute the following line in your script:

mysql database.name < scriptfile.txt > /home/divya/Desktop/Data.xml

---

### Post by Bachstelze on 2012-07-20
You might want to read more about the usage of the *-p* option of the MySQL command-line client...

@sudodus: when you have no idea what you are doing, as you admit yourself, please do not tell people to run things with sudo.

---

### Post by Wim Sturkenboom on 2012-07-20
Create a new mysql user (without password) that has exactly the permissions on databases and tables that are required (select only). Use that user in your scripts.

That way you never have to reveal passwords for simple stuff like selects.

On a side note:
the mysql root user should only be used when strictly necessary; e.g. when granting permissions and creating empty databases. Create other users that can basically create tables etc inside the database(s). And create a mysql user that can use those tables (without modifying the structures etc). You can finetune it to your needs.

In my setup, I use root to create databases and grant permissions to the developer (being myself) to do anything with the database. The root user also sets up grants for other users (select, insert etc) for the specific database.

---

### Post by Bachstelze on 2012-07-20
> **Wim Sturkenboom said:**
> 
In my setup, I use root to create databases and grant permissions to the developer (being myself) to do anything with the database. The root user also sets up grants for other users (select, insert etc) for the specific database.

This is certainly the best way to go. It's very easy, too; for example with phpmyadmin, when you create a user, you have a "create database with the same name and grant all privileges" option, which is pretty self-explanatory. Even better: create one user/database pair for every application (e.g. a 'wordpress' database, a 'phpbb' database, etc.).

---

