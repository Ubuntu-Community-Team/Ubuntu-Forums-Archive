---
title: "[SOLVED] Any best software for Mysql"
date: 2008-03-04
forum: Programming Talk
---

### Post by mmarif4u on 2008-03-04
Hi to all here.
I am programming in PHP with mysql.
I just install Ubuntu.i find it nice.
I install xampp on it.it has phpmyadmin.
But i want another software,bcoz of big size database to restore and backup.Software like mysql query browser and mysql administrator.
I use these on window system b4.its nice to work with.
So any body have any idea.

Thanks in advance.

---

### Post by mmarif4u on 2008-03-04
i install it by using the following command in terminal.

> sudo apt-get install mysql-admin

And it install it perfectly.
Now when i am trying to login to it,it says
"Can't connect to host 'localhost'".
how can i fix it.

---

### Post by mmarif4u on 2008-03-05
Any body have any idea.

---

### Post by neoAnderson on 2008-03-05
Are you sure your mysqld is running? I just installed mysql-server using sudo apt-get install and then when I tried to connect to mysql-administrator it complained that it cannot connect to localhost. So then I ran mysqld in the background and then I was able to connect to the server using mysql-administrator. And when I restarted my machine now mysql server starts at the beginning automatically and I have no problems whatsoever.

---

### Post by mmarif4u on 2008-03-05
Tq for ur reply.
How can i start mysqld.

---

