---
title: "NetBeans IDE 6.8 &amp; mySql in UBUNTU 10.4"
date: 2010-06-05
forum: Programming Talk
---

### Post by MughalShahzad on 2010-06-05
Hello,
I installed NetBeans IDE 6.8 from Software Center of UBUNTU 10.4, then I installed following plug ins

[LIST=1]
[*]Database
[*]Java Web Application (automatically selected its required plug ins)
[/LIST]
I got a tutorial to install LAMP, PHP, PHPADMIN from following URL

[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)

now I have NetBeans IDE and mySQL in its services, I have created tables, inserted data into them, but could not view data.

Is this right method to install all these things and why not I am able to view data?

If some one have more appropriate method to prepare system for java app/web development please do suggest me.

Thanks & Regards
Shahzad

---

### Post by v1ad on 2010-06-05
how are you trying to view it.

---

### Post by .:PiXi²:. on 2010-06-05
Can you view the tables using phpmyadmin?

---

### Post by MughalShahzad on 2010-06-05
no, its not working

---

### Post by MughalShahzad on 2010-06-05
from within NetBeans IDE Services > Databases > jdbc:mysqk://localhost:3306/myDB[root on Default Schema] > right click and Connect > myDB > Tables

tables (default and created) are being shown, when I put insert statement system says that Executed successfully in 0.039 s, 1 rows affected. does not show data.

when I tried to insert record with duplicate primary key it refuses and says that Error code 1062, SQL state 23000: Duplicate entry '1000' for key 'PRIMARY'

---

### Post by G-Fresh on 2010-11-12
> **MughalShahzad said:**
> 
tables (default and created) are being shown, when I put insert statement system says that Executed successfully in 0.039 s, 1 rows affected. does not show data.


I've got a similar problem.  Is there another window which you have to select to view the data?  I was expecting it to appear in the space where the above message appears.

---

