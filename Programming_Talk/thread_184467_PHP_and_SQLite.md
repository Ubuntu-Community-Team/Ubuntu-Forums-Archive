---
title: "PHP and SQLite"
date: 2006-05-29
forum: Programming Talk
---

### Post by flightcrank on 2006-05-29
Hi, im looking for some documentation to get started with PHP and SQLite.

I have a general knowledge of PHP but most books I have speak of mySQL ect..

I know there are only a few minimal differences, but im still a beginner and would prefer to have specific documentation regarding using PHP together with SQlite. with explanations as to _why_ particular things work the way they do ect.

also is it possible to get Open Office 2.  to open and edit SQLites filename**.db** files ?

also I have php5 in witch SQlite comes bundled with. I can create edit tables with the databases no problem from with PHP code.

but I can&#8217;t edit the same database files from the command line. I have installed the appropriate package to do this. but little or no documentation comes with the command line client. for example I have a /var/www/database/filename.db

how do I edit that from console ? to create/open a file its 

```
SQlite filename.db
``` I can do that fine it writes it to my home directory

so I assume you would simple do a 

```
SQlite /var/www/database/filename.db
```

but that dosnt seem to work.

any way more importantly I would really like to be pointed to the way of some good in-depth books or resources for beginners using PHP and SQlite maby even more importantly what can be accomplished buy using them

THANKS !

---

### Post by Corvillus on 2006-05-30
It could be a privileges issue. If your user doesn't own /var/www, it can't write to it, so you'd have to use sudo to access it. Also, on a different note, storing your SQLite database under /var/www or any other web-accessible directory might not be a good idea for security reasons, it might be better to store it somewhere else on the disk, and just give it permissions so that PHP can access it.

---

### Post by flightcrank on 2006-05-30
Thanks for the tip. my root directory is 

/var/www/html

so i assume its safe in /var/www/databse/

---

