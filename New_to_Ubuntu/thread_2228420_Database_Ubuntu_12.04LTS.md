---
title: "Database Ubuntu 12.04LTS"
date: 2014-06-07
forum: New to Ubuntu
---

### Post by florisrei on 2014-06-07
Hi,

How do I resolve this?


```
An error occurred while upgrading the database:                              
 &#9474;                                                                              
 &#9474; ERROR: duplicate key value violates unique constraint                        
 &#9474; "pk_databasechangelog" DETAIL: Key (id, author,                              
 &#9474; filename)=(change-column-notes-in-task_element-to-text, jaragunde,           
 &#9474; src/main/resources/db.changelog-1.3.xml) already exists.                     
 &#9474;                                                                              
 &#9474; Fortunately, /var/cache/dbconfig-common/backups/libreplan_1.3.0-1.pgsql      
 &#9474; holds a backup of the database, made just before the upgrade.                
 &#9474;                                                                              
 &#9474; If at this point you choose "retry", you will be prompted with all the       
 &#9474; configuration questions once more and another attempt will be made at        
 &#9474; performing the operation. "retry (skip questions)" will immediately          
 &#9474; attempt the operation again, skipping all questions.  If you choose          
 &#9474;                                                                        

```

---

### Post by grahammechanical on 2014-06-07
Is this with the database component of Libreoffice?

---

### Post by florisrei on 2014-06-07
Yes it is:D

---

### Post by florisrei on 2014-06-07
I installed Libre Plan and cannot get the database to set-up correctly - above is the message I get.  Can someone help me to solve this?

---

### Post by kansasnoob on 2014-06-07
Did you use a PPA?

The source of the download would be helpful.

---

### Post by florisrei on 2014-06-09
No I did the following:

```
wget http://downloads.sourceforge.net/project/libreplan/LibrePlan/libreplan_1.3.0-1_amd64.deb
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get upgrade

```

Thank you

---

### Post by Vladlenin5000 on 2014-06-09
You didn't actually installed it. Are you aware of that? 'install -f' just install pending updates.

---

### Post by florisrei on 2014-06-10
Sorry Posted the wrong one.

```
sudo apt-get install libreplan
```

---

### Post by mastablasta on 2014-06-10
that line would install the one in the repositories not the file you downloaded. so which version you have? to intall downloaded file open it with software center or double click the downloaded file.

---

