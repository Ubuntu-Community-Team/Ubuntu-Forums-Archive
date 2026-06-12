---
title: "PHP file access permissions..."
date: 2009-02-02
forum: Programming Talk
---

### Post by Stoneyhill on 2009-02-02
Hi

Im using php (on lamp) on localhost to try and teach myself php with the help of a book,  on Intrepid Ibex and so far all has been working well... 

HOWEVER..

when i am trying to read and write to files with php im having some problems

	```
$fp = fopen("http://localhost/orders.txt", 'r');
```

works fine and i can read the file without ANY problems, however if i want to use:

```
$fp = fopen(“$DOCUMENT_ROOT/../orders/orders.txt”, ‘w’);
```

or even an absolute path such as /var/www/orders.txt

i get the following error:

> 
Warning: fopen(/var/www/orders.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/processorder.php on line 72


can anyone tell help me understand what is going on here...? if its something to do with apache permissions then can anyone tell me how to change them etc... 

NOTE without the use of ```
sudo
``` in the command line i cannot edit ANYTHING in the /var/www directory at all so thought perhaps that was the issue, however when i used an absolute path to a file outside /var/www i get a similar error.... 


thanks

---

### Post by johnl on 2009-02-02
Apache (and thus any php scripts) will run as the user 'www-data' with the group 'www-data'.  This user or group will need write access to whatever file you want to write to.  Generally, all the files in your /var/www should be owned by www-data, but they should probably not be writable by default for security reasons.  

[This page](http://www.dartmouth.edu/~rc/help/faq/permissions.html) has a pretty good overview of permissions if you need more information.

It is totally normal that you should not be able to read/write files in places outside of your home directory without using root permission (eg, sudo).  Imagine if any user on the system could edit system files.

---

