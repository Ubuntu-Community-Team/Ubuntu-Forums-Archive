---
title: "[SOLVED] Second Brick Wall (Apache+PHP5)"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ingeva on 2008-07-27
Thanks for all help with Apache!
I have now set it up with 9 virtual hosts, which work nicely with html files but not with php.

I have followed all directions I have found (many are different) but Firefox asks what program should be used to open PHTML (?) files or BIN files (if I remove the application definitions in .../mime.types.

I'm again quite lost.
(Running Ubuntu 8.04 desktop and FireFox 3.0. Apache 2.2.8.).

---

### Post by ingeva on 2008-07-28
> **ingeva said:**
> Thanks for all help with Apache!


After trying and retrying for hours I decided to re-install the whole system,
so I saved my config files and did.

This time it was easy, and php runs fine -- except my scripts can't create files
but that's just a beginner problem.

---

### Post by stevoo on 2008-07-28
what i was thinking was the .mime types. 
Have they changed in your file ? 

if you remember offcourse

---

### Post by ingeva on 2008-07-28
> **stevoo said:**
> what i was thinking was the .mime types. 
Have they changed in your file ? 

if you remember offcourse

No, the mime.types file is the same as original.

The reason why php wouldn't work was probably that a couple of files (php5.conf and php5.load) were missing in the /etc/apache2/mods-enabled directory.
When I installed again these files were saved correctly.

---

### Post by noman1207 on 2008-07-29
Hi 

I am trying to set up virtual host with apache but getting this error can any one help me out

apache2: Syntax error on line 299 of /etc/apache2/apache2.conf: Syntax error on line 20 of /etc/apache2/sites-enabled/domain1.com: Expected </VitualHost> but saw </VirtualHost>
   ...fail!

line 299 is
Include /etc/apache2/sites-enabled/

---

### Post by ingeva on 2008-07-29
> **noman1207 said:**
> apache2: Syntax error on line 299 of /etc/apache2/apache2.conf: Syntax error on line 20 of /etc/apache2/sites-enabled/domain1.com: Expected </VitualHost> but saw </VirtualHost>
   ...fail!

line 299 is
Include /etc/apache2/sites-enabled/

Line 299 means that all the files in that directory will be read. The file 
/etc/apache2/sites-enabled/domain1.com contains a typo in line 20: </VitualHost>
(should be </VirtualHost.)

I see that the right and the wrong spelling have switched around, but the message is otherwise clear.

---

