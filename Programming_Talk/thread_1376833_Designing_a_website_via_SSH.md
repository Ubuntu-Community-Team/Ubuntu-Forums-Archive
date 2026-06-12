---
title: "Designing a website via SSH"
date: 2010-01-09
forum: Programming Talk
---

### Post by DanielJackins on 2010-01-09
Hello,

I am trying to design a website, and the only way I can do it is via SSH (I have a domain provided by a University, and I am not at the University). I'm not sure what it has installed, but I know it can handle PHP and it has some way of integrating Python with HTML (though I forget what it's called). I was wondering if there was any way I could implement some sort of forum or discussion board using what is available to me.

Thanks for any help

---

### Post by Finalfantasykid on 2010-01-09
If you are using Ubuntu, just go places > connect to server.

Select Service Type as SSH(FTP will probably work as well), and then enter the server address and your credentials etc.

Then you should get a nautilus window open up with all your folders on there.  Just edit your php/html files this way, and it will update on the server once that file is saved.

Or if you want to do everything via the terminal, I would suggest using sftp.  That way you can upload/download files over your computer.  But writing code might be more difficult this way, you would probably have to know how to use vim, or you could write the code on your computer, then upload it.

EDIT:  One thing the university might not have available to you is a database.  If you want a forum, you would need a database of somesort.

---

### Post by The Secret on 2010-01-09
Wouldn't it be simpler to design it on your own computer and then copy it to the remote server through SSH ?

---

### Post by DanielJackins on 2010-01-09
Yeah that's probably a better idea :P I'm new to all this.

> **Finalfantasykid said:**
> If you are using Ubuntu, just go places > connect to server.

Select Service Type as SSH(FTP will probably work as well), and then enter the server address and your credentials etc.

Then you should get a nautilus window open up with all your folders on there.  Just edit your php/html files this way, and it will update on the server once that file is saved.

Or if you want to do everything via the terminal, I would suggest using sftp.  That way you can upload/download files over your computer.  But writing code might be more difficult this way, you would probably have to know how to use vim, or you could write the code on your computer, then upload it.

EDIT:  One thing the university might not have available to you is a database.  If you want a forum, you would need a database of somesort.

Is there any way I can check if they have a database?

---

### Post by Finalfantasykid on 2010-01-09
SSH into the university server(via terminal), and type mysql(If they do have a database for you, this is probably it), and see if it says anything interesting.  If it says command not found, then they might be using a different type of database, or none at all.

---

### Post by DanielJackins on 2010-01-09
Okay, it gave me this:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)

---

### Post by The Secret on 2010-01-09
```
mysql -h localhost -u root -p

```

If it asks for a password, you are ready to go.

---

### Post by DanielJackins on 2010-01-09
Gives the same error. It asks for a password, so I enter my (user?) password, but gives the error afterwards. I don't have administration privileges.

---

### Post by Finalfantasykid on 2010-01-09
Ok well it looks like it does have a mysql database.  Try this

```
mysql -u yourUserName -pyourPassword -h mysql.universityDomain
```Notice there is no space after the -p

Also this is a pretty big if, you might(probably) are not allowed access to the database, or the database is not actually located at mysql.universityDomain.  You could always email somebody at the university about accessing it.

EDIT:  Looking at your above post, it looks like you are in fact not allowed to access the database.  You could always email the university though...

---

### Post by Hellkeepa on 2010-01-10
HELLo!

Never use the password to the database directly in the command line on a shared host, doing it will allow other people to see it when using "top" or "ps".

The error message given above usually means one of these three things:
[list][*]The MySQL server is not installed on the computer.
[*]The MySQL server is not running, yet.
[*]The socket file is located elsewhere, usually "/tmp/mysql.sock", and the MySQL client does not know where to look.[/list]
All three are only correctible by the server administrator, so I recommend getting in touch with them and asking them how to connect to their MySQL server, if they have one.

Happy codin'!

---

