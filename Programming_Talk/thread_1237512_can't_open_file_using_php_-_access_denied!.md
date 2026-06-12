---
title: "can't open file using php - access denied!"
date: 2009-08-11
forum: Programming Talk
---

### Post by kapi on 2009-08-11
Hello there,

Am working on some php and learning how to use fopen() and fwrite()

however when I open the document in the browser I receive


Warning: fopen(textfiles/coyunt.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/php_tests/PHP_Academy/tutorials/unique_visitor_counter.php on line 38

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/php_tests/PHP_Academy/tutorials/unique_visitor_counter.php on line 41

Warning: fopen(textfiles/ips.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/php_tests/PHP_Academy/tutorials/unique_visitor_counter.php on line 43

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/php_tests/PHP_Academy/tutorials/unique_visitor_counter.php on line 44

Can someone shed some light please. :-)

---

### Post by Mirge on 2009-08-11
Have you checked permissions?

---

### Post by kapi on 2009-08-11
Well at the moment I have full access to read and write to the var folder containing www and my files for php so i'm really confused. If I didn't then when I try to save changes to an existing open document say in Geany then I'd get error messages and permission denied. 

I know it'll be something really stupid but I'm at a loss

---

### Post by Mirge on 2009-08-11
> **kapi said:**
> Well at the moment I have full access to read and write to the var folder containing www and my files for php so i'm really confused. If I didn't then when I try to save changes to an existing open document say in Geany then I'd get error messages and permission denied. 

I know it'll be something really stupid but I'm at a loss

Are you running the script(s) via apache? If so, the user apache is running as isn't the same as what you log in & do things as.

---

### Post by kapi on 2009-08-11
I have my php page held in the www folder. The index page tries to open a simple .txt file held in another folder within the www folder

eg:

www folder holds:

    textfiles folder - this holds a simple text document

    index.php - this tries to open the simple text file in textfiles

---

### Post by hessiess on 2009-08-11
Chown the files to the same user as Apache, or get php running as the user that owns the files with CGI/FastCGI and suexec. The first is simpler, the second is more secure if the server has more than one user.

---

### Post by kapi on 2009-08-11
I've opened the folder (php_tests) as administrator, its permissions are not set as root but rather to kapi(me) 

The folder access is set to create and delete but the file access is set to --   

It won't let me set the file access to read and write

---

### Post by kapi on 2009-08-11
Actually the txt files themselves do have read-write access- 

still perplexed though

---

### Post by hessiess on 2009-08-11
open a command line, then run

```

sudo chown -R http:http /var/www
sudo chmod -R 777 /var/www

```

You may need to change http:http, On Arch Apache runs as the user `http', however I cannot remember if Ubuntu uses `http' or some other user. The second command changes the permissions so that a file can be read,write, and executed by every user, do not set the permissions like this on a shared server.

---

### Post by kapi on 2009-08-11
Thanks hessiess,

I didn't do what you asked because I was mucking around with the permissions while you were commenting, however while changing the permissions in the .txt files I noticed that if I set the permissions for 'others' to read and write then all works ok.

I was wondering though, isn't it unsafe to set the permissions for others to read and write? Or is that just a setting for my machine, what happens when I upload to the server on the net? am I leaving myself open to abuse?

Thanks for your help by the way :-)

---

### Post by hessiess on 2009-08-11
It would be a problem if you were running a shared hosting server, as it would allow one user to edit another users files, and it could be a problem if you were running an exploitable PHP or CGI application, which would potentially allow the attacker to mess with all of the files on the server. However as long as you are careful(be sure to filter all user supplied input correctly) you shouldn't have a problem.

Personally I would recommend that you don't ever store data in the file system, only the database, and leave the file permissions as read-only.

---

