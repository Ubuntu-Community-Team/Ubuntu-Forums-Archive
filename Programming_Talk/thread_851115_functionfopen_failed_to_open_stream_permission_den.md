---
title: "function:fopen failed to open stream permission denied"
date: 2008-07-06
forum: Programming Talk
---

### Post by caseyann on 2008-07-06
Hello all,
I'm a php/ubuntu/apache/mysql n00b and I'm receiving this error when attempting to write to a file:

> Warning: fopen(/usr/local/apache/htdocs/students/boesen/ch06/dummy.txt) [function.fopen]: failed to open stream: Permission denied in /home/caseyann/students/boesen/ch06/writefile.php on line 6
Could not open file!

I'm assuming this has to do with write permissions, but I'm not sure where to start to solve this problem. 

My setup is only for dev purposes. Using Ubuntu Hardy 8.04/Apache 2.2/PHP 5.0/MySQL 5.0.

Yes, I've made sure the file exists :)

Any help would be appreciated!
Caseyann

---

### Post by henchman on 2008-07-06
Hello! :)

your server (eg. apache) needs to have write permission to the file. the easiest way to check this is set the file permissions to 777 (everybody has read/write access).

if you want to create new files in this folder with php, the server also needs to have write permissions to the folder

edit: 
you get information on each bash-command using
```
man command
```
eg.
```
man chmod
```
, where chmod is the command to change the file/folder permissions.

---

### Post by -grubby on 2008-07-06
> **henchman said:**
> Hello! :)

your server (eg. apache) needs to have write permission to the file. the easiest way to check this is set the file permissions to 777 (everybody has read/write access).

if you want to create new files in this folder with php, the server also needs to have write permissions to the folder

That is not recommended, you should probably set it to 644 permissions

---

### Post by caseyann on 2008-07-06
I agree 777 isn't the best answer. Couldn't I add the Apache server user to my group? Would that give the server write permissions to my .php files?

---

### Post by sipickles on 2008-10-02
I'd like to bump this.

How do I make apache a member of a group with read/write access for the folder my website is in?

Thanks

Simon

---

### Post by xakira on 2010-07-26
I believe this could help:-

The apache user is in a group called "www-data" so you could assign this group to your "www" directory as follows

NOTE: don't do the following command if your mysql data directory resides in your www or sub directory of www!  It wont be there by default unless you have moved it there yourself.

"sudo chgrp -R www-data /path/to/your/www"

That command changes all subdirectories and files to be in the group "www-data"

Then make sure all the sub directories and files have read/write for user and group as follows

"sudo chmod -R 775 /path/to/your/www"

Hope that helps.

Xak

---

