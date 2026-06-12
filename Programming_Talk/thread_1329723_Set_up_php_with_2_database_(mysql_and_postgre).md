---
title: "Set up php with 2 database (mysql and postgre)"
date: 2009-11-17
forum: Programming Talk
---

### Post by play05 on 2009-11-17
Hai everyone. :D

My postgresql didn't work with php but mysql work.
May i know if there got another way to make both database works with php?


Thanks

Play

---

### Post by MonoDeem on 2009-11-17
What exactly didn't worked ?

---

### Post by play05 on 2009-11-17
Thanks for quick reply

I had to install phppgadmin.
And got error
"Your PHP installation does not support PostgreSQL. You need to recompile PHP using the --with-pgsql configure option"

I used apt to install PHP
Therefore, I don't have any of the original source files. Can someone please provide a suggestion or steps to recompile PHP
Then after recompile php can it still connecting to mysql?

---

### Post by akvino on 2009-11-17
> **play05 said:**
> Thanks for quick reply

I had to install phppgadmin.
And got error
"Your PHP installation does not support PostgreSQL. You need to recompile PHP using the --with-pgsql configure option"

I used apt to install PHP
Therefore, I don't have any of the original source files. Can someone please provide a suggestion or steps to recompile PHP
Then after recompile php can it still connecting to mysql?

I know you can connect to both with php-pdo object.

---

### Post by CyberJack on 2009-11-18
You don't need to compile php.
Have you installed the php5-pgsql package?

---

