---
title: "Adding Comment boxes using MySQL and PHP?"
date: 2010-04-18
forum: Programming Talk
---

### Post by ZJ88 on 2010-04-18
I have website hosting on my Ubuntu my server with Apache2, php, and  MySQL. What I want to do is add a comment section under a post or video  so anyone can comment.  I don't need them to be logged into anything  (though it would be nice in the future).  The problem is, I know very  little of PHP and MySQL.  Can anyone help find a way to get a comment  section running?

---

### Post by Simon17 on 2010-04-19
Do you want to be able to write it yourself, or do you just want comments?
There are plenty of ready-made solutions already available. Search for "php comment script" or something like that and you should find a ton of them.

---

### Post by ZJ88 on 2010-04-19
I just want people to comment.  I'll have to look around and find some. Thanks for the help, but is there anything I need to set up in an MySQL database or will the php suffice?

---

### Post by help_me_please on 2010-04-19
i you want to display the comments (like on youtube for example) which is what i understand from your question, you will need a database in which to store the comments so the php script has from where to retrieve them and display them on the page. the type of database will depend on the ready-made script you will choose to incorporate. it is very likely that you will need to set up a mysql database. it is possible that there are ready made scripts that provide some form of setup procedure that, when given mysql login data, will handle database and table creation for you.
if, on the other hand, you want users to be able to send you comments that do not have to be displayed in the future, then a script that just sends user comments to an admin email address would probably be what you want, which requires no database.

---

### Post by ZJ88 on 2010-04-20
I got this working actually.  I used a gentlesource script.  I also remembered I had installed phpmyadmin and set up a database so it was a matter of changing my pages to php extensions and changing the script to what I wanted the colors and such to be.  Thanks for the help guys

---

