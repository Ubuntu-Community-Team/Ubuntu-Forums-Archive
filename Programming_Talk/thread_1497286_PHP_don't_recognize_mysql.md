---
title: "PHP don't recognize mysql"
date: 2010-05-30
forum: Programming Talk
---

### Post by aklo on 2010-05-30
I got apache, mysql, php working ...I can go to localhost, I can go into mysql and create my databases and tables. Apache can also load .php files.

Problem is, I used this code:

[PHP]
$con = mysql_connect("localhost", "root","");
if (!$con) {
    echo ("Could not connect" . mysql_error() );
}else {
    echo ("Connected successfully");
}

?>
[/PHP]

I just want to test if I could connect to mysql but there does not seem to load any message...because it should tell me if i failed or if I succeed in connecting to the database...but I don't see any message...Error reporting is turned on in my php.ini file.


Also I think it should be something to do with the PHP and MYSQL extension...I could not find mysql.so / mysqli.so anywhere. Also i'm not sure which part of php.ini i should edit which is located in /etc/php5/apache/php.ini   ....so if anybody can tell me how can i get the mysqli.so file and the appropriate php.ini file to edit....

Thank you.

---

### Post by januzi on 2010-05-30
Did You install php5-mysql ?

---

### Post by aklo on 2010-05-30
Ah thanks! Yup i forget to install that...i thought i did even though i don't know that it gives the mysql.so file...

---

