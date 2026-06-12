---
title: "PHP - Apache permissions confussion"
date: 2006-08-04
forum: Programming Talk
---

### Post by nroussi on 2006-08-04
Hi, I have a few php pages that are running on Apache and are pulling data from a MySQL DB. Viewing the pages are not a problem. In one of the pages I use the mkdir function to create directories and I am getting permission denied error. I have tried the following:
-chown -R root:root -mydir-
-chmod -R 777 -mydir-
did not work. Then I tried:
-chown -R www-data:www-data -mydir-
-chmod -R 777 -mydir-
and it did not work again. The directory is in /var/www/mydir
Following is the output of the ls -la:
drwxr-xr-x  5 root root 4096 2006-08-03 18:14 .
drwxr-xr-x 15 root root 4096 2006-08-02 21:47 ..
drwxr-xr-x  2 root root 4096 2006-08-02 16:37 apache2-default
lrwxrwxrwx  1 root root   21 2006-08-03 15:48 phpmyadmin -> /usr/share/phpmyadmin
**drwxrwxrwx  3 root root 4096 2006-08-04 02:04 teachers**
drwxr-xr-x  2 root root 4096 2005-10-29 00:47 tmp
The directory in question is the bolded line. I have another Ubuntu installation and it works fine. Same directory structure and exact same files. The permissions are the same also. 
Can anyone please help?#-o

---

### Post by ifokkema on 2006-08-04
Did you modify the Apache/PHP configuration?
Did you try and touch a file in stead of an mkdir?
[PHP]<?php
var_dump(touch('/var/www/teachers/test'));
?>[/PHP]
Did you check the Apache error log?

---

### Post by nroussi on 2006-08-04
I know this is stupid but where are the Apache log files located?
--never mind=; I found it. /var/log/apache2
Now that I found it what am I supposed to be looking for?

---

### Post by ifokkema on 2006-08-04
> **nroussi said:**
> I know this is stupid but where are the Apache log files located?
That's not stupid :)
You may have found this out already, but most log files are found in /var/log (system, daemons, X, Apache, etc).

> **nroussi said:**
> Now that I found it what am I supposed to be looking for?
Basically anything that corresponds to the time you tried it. So if the system time is 20:14:43 when you call the script, check for entries just around this time, and post the contents. There is not necessarily anything in there related to the error, though.

Did the touch file work, or did that fail as well? What did you get returned on screen?

---

### Post by nroussi on 2006-08-04
Thanks for the reply. This is the output of the touch function:
Warning: touch() [function.touch]: Unable to create file 
2RU/Debesa because No such file or directory in /var/www/teachers/upload.php on line 38
bool(false) 
This is the entry in the apache log:
192.168.1.6 - - [04/Aug/2006:14:53:45 -0400] "GET /teachers/upload.php?ID=1&theName=Debesa&theClassName=2RU HTTP/1.1" 200 533 "http://192.168.1.2/teachers/teacherDetails.php?ID=1" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.1)"
Also, you mentioned modifying the Apache/PHP config. Everything is working properly. The PHP pages are diplayed with no problems.
Thanks

---

### Post by ifokkema on 2006-08-04
> **nroussi said:**
> This is the output of the touch function:
Warning: touch() [function.touch]: Unable to create file 
2RU/Debesa because No such file or directory in /var/www/teachers/upload.php on line 38
bool(false)
If I read this correctly, it tries to create /var/www/teachers/2RU/Debesa, but is there a /var/www/teachers/2RU directory? If not, it's not going to work ;)

---

### Post by nroussi on 2006-08-04
If there is a 2DE directory it gives me a permission denied to create the /Debesa directory. If there is not then it tells me that no such file or directory exists when trying to create /2DE/Debesa.

---

### Post by ifokkema on 2006-08-04
> **nroussi said:**
> If there is a 2DE directory it gives me a permission denied to create the /Debesa directory. If there is not then it tells me that no such file or directory exists when trying to create /2DE/Debesa.
OK, back to square one because I'm just not sure I'm getting it.
- Is it /var/www/teachers/2DE or /var/www/teachers/2RU???
- If you're trying to create something in either of these directories, what's the output of:
```
ls -lah /var/www/teachers/
```

---

### Post by nroussi on 2006-08-04
this is the output:
root@octagon1:~# ls -lah /var/www/teachers
total 356K
drwxrwxrwx 5 root     root     4.0K 2006-08-04 15:46 .
drwxr-xr-x 5 root     root     4.0K 2006-08-03 18:14 ..
drwxrwxrwx 3 root     root     4.0K 2006-08-04 01:43 2DE
drwxr-xr-x 2 root     root     4.0K 2006-08-04 15:06 2RU
-rwxrwxrwx 1 www-data www-data 285K 2006-08-04 15:08 cl_20060804_3199.doc
-rwxr-xr-x 1 root     root     4.8K 2006-08-03 19:04 default.php
-rwxr-xr-x 1 root     root     4.8K 2006-08-03 19:04 default.php~
drwxr-xr-x 2 root     root     4.0K 2006-08-04 15:46 KFR
-rwxr-xr-x 1 root     root      139 2006-08-04 01:44 log.txt
-rwxr-xr-x 1 root     root     5.2K 2006-08-03 19:04 teacherDetails.php
-rwxr-xr-x 1 root     root     5.2K 2006-08-03 19:04 teacherDetails.php~
-rwxr-xr-x 1 root     root     6.8K 2006-08-04 15:14 upload.php
When I call upload.php which is in the /var/www/teachers directory I need it to create directories in it and subdirectories. For example: if the teacher that requested the upload.php file is Debesa and teaches section 2DE then I need it to create 2 directories if they are not created. First /var/www/teachers/2DE and then /var/www/teachers/2DE/Debesa. Now if the teacher that requests upload.php is again Debesa but is for the section 2RU then I need to create 2 other directories /var/www/teachers/2RU/Debesa. I think I am just going to go ahead and create the directories manually. If I create them logged in as root it works.

---

### Post by ifokkema on 2006-08-05
Judging from this line, the script should be able to create a directory for a section:
> **nroussi said:**
> 
drwxrwxrwx 5 root     root     4.0K 2006-08-04 15:46 .


However, these section directories are not writable by the webserver:
> **nroussi said:**
> 
drwxr-xr-x 2 root     root     4.0K 2006-08-04 15:06 2RU
drwxr-xr-x 2 root     root     4.0K 2006-08-04 15:46 KFR

So creating teacher directories in those is not possible.
Try, logged in as root or with sudo,
```
chown -R www-data:www-data /var/www/teachers
```

That should really solve the problem... :???:

---

### Post by nroussi on 2006-08-05
Thanks for your help. \\:D/
I did that but I also changed the PHP code to create the first directory and chmod it to 755. Then I created the second and chmod that to 755 and now everything is working perfectly.
Thanks again

---

### Post by ifokkema on 2006-08-06
Good to hear you got it to work! :KS

---

