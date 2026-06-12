---
title: "Ant deploy.xml"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by anderskitson on 2008-06-24
> ant –f deploy.xml <target_name>

Following table describes the different targets of the ANT script:
Deploy-all
To install the application and the database
DBInitialize
To install the database only
Deploy
To install the application only
Table 4

I am following documentation to install a database program for a medical lab, anyhow, when I enter in > ant -f deploy <Deploy-all> I get syntax errors, but when i just type in > ant -f deploy.xml, I get build failed Deploy does not exist, which it does exist and I have cd into the correct directory. I am stuck

---

### Post by pytheas22 on 2008-06-24
I have no idea what this program is, but if you can link to or post the documentation (and if possible the software itself), I can take a look and maybe make a suggestion.

---

### Post by anderskitson on 2008-06-24
[http://gforge.nci.nih.gov/frs/?group_id=18](http://gforge.nci.nih.gov/frs/?group_id=18)
In catissue release 1.01
Program ([catissue_core_installable.zip]("http://gforge.nci.nih.gov/frs/download.php/628/caTissue_Core_Installable.zip")) 
Documentation ([caTissueCoreDeploymentGuide.doc]("http://gforge.nci.nih.gov/frs/download.php/631/caTissueCoreDeploymentGuide.doc"))

---

### Post by pytheas22 on 2008-06-24
I think the command you need to use is:
```

ant -f deploy.xml deploy_all_with_config
```

('deploy_all_with_config' could be replaced by a couple other options depending on what you want to install; see the table on pages 8-9 for the other options)

and make sure you're cd'd into the directory containing the files.  I didn't actually build the file because I didn't bother to fill in the pre-installation configuration file, but it looks like it would build if that file were filled in.

If you run into more trouble, please post.

---

### Post by anderskitson on 2008-06-25
That definitely seemed to fix the problem to a certain point. I am getting build failed, but only at the end, i probably am entering a wrong value in one of the properties file. I will keep trying different things, unless you have an ideas.
> 
BUILD FAILED
/usr/local/caTissue_Core_Installable/deploy.xml:397: The following error occurred while executing this line:
/usr/local/caTissue_Core_Installable/deploy.xml:405: The following error occurred while executing this line:
/usr/local/caTissue_Core_Installable/deploy.xml:427: java.sql.SQLException: Invalid authorization specification message from server: "Access denied for user 'catissue_core	'@'localhost' (using password: YES)"


---

### Post by pytheas22 on 2008-06-25
> java.sql.SQLException: Invalid authorization specification message from server: "Access denied for user 'catissue_core '@'localhost' (using password: YES)"

It sounds like the credentials you entered for your database account (I guess it's a mysql database? but I might be wrong as I don't have any experience with java-based stuff like this) are incorrect.  Make sure you put them in correctly.

I also notice that it thinks your username is "catissue_core " (notice the blank space on the end).  Maybe you need to delete the blank space from the configuration file.

---

### Post by anderskitson on 2008-06-26
I have just unistalled, and reinstalled mysql database. Now I cant seem to login

> lab471@lab471-desktop:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
lab471@lab471-desktop:~$ mysql -u root -p



There is a MySql_DB_Creation.sql file in the caTissue Deploy folder, now is this something I have to manually install in mysql, or should it be deployed during the build with ANT. THis is what the file contains

> CREATE DATABASE {catissue};



GRANT ALL PRIVILEGES ON *.* TO ‘{catissuecore}'@'localhost’ IDENTIFIED BY '{catissue_core}' WITH GRANT OPTION;



GRANT ALL PRIVILEGES ON *.* TO '{catissuecore}'@'%' IDENTIFIED BY '{catissue_core}' WITH GRANT OPTION;,

  since I cant seem to login into mysql, I cant do it manually, I thought there wasn't a defualt password, but i ahve tried blank and it doesn't work.

---

### Post by pytheas22 on 2008-07-02
Sorry, I lost track of this thread; I wasn't ignoring you on purpose.  Did you figure out the problem yet?  If not, let me know which point you're at now and I'll see if I have any suggestions.

---

