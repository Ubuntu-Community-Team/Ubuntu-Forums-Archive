---
title: "mysql injection..."
date: 2006-02-14
forum: Programming Talk
---

### Post by grim918 on 2006-02-14
i was wondering if their is a php or mysql function that will add a backslash to single/double quotes in order to prevent sql injection attempts. i only know of the stripslashes(), but that only removes backslashes and leaves behind the single/double quotes, this creates a problem when you try to enter the string into the database. I would appreciate any help with this problem.

---

### Post by tenshu on 2006-02-14
huhu
addslashes()

if anyone have something more simple i'll make a donation
=)

---

### Post by LordHunter317 on 2006-02-14
Use the mysqli driver, PEAR::DB, ADODB and parameterized queries.  If you're escaping strings yourself, you're doing something wrong.

---

### Post by grim918 on 2006-02-14
addslashes() thats it. im such an idiot. that will add slashes to all single/double quotes. thankz for the help. ill try it out once i get home from school.

---

### Post by LordHunter317 on 2006-02-14
**No, don't use that, as it will get things wrong.**  Do what I say, or if you're hellbent on using the plain mysql driver for whatever reason, at least use mysql_real_escape_string.

---

### Post by grim918 on 2006-02-14
how do i do what your telling me to do. i don't understand the different kinds of mysql drivers that your talking to. I'm new to programming. Is there somewhere i can read about what your telling me. and why is using addslashes() wrong. i tried it and it works but, if you say its no good then ill do something else. I don't want to develop some bad programming habits. thank you for your help.

---

### Post by LordHunter317 on 2006-02-14
[QUOTE=grim918]how do i do what your telling me to do. i don't understand the different kinds of mysql drivers that your talking to.[/quote]PHP itself ships two MySQL drivers: Mysql, which uses the mysql_* family of functions, and mysqli which is a class that performs similar functionality.  You should use always use mysqli over mysql.  Both are documented on php.net.

PEAR::DB is a class that helps to provide database indepedence, as does ADODB.  Both can be found on line via google.

> I'm new to programming. Is there somewhere i can read about what your telling me. and why is using addslashes() wrong.Quoting a SQL query involves more than just addslashes, sometimes.  More importantly, every DB is different and addslashes is programmed to the lowest common denominator.

---

### Post by ZylGadis on 2006-02-15
.

---

### Post by LordHunter317 on 2006-02-15
[QUOTE=Alex.P]I believe he was asking for a resource written by somebody more renowned than your omniscient figure?[/quote]For addslashes()?  Simple.  Some databases don't use slashes at all to escape single quotes, but rather use another single quote.   So the literal:```
My Mother's Name'
```Becomes:```
'My Mother''s name'
```when quoted.  The PostgreSQL documentation will confirm this.  As will the php.net documentation for addslashes(), which he would know if he (and you) had read it.

More importantly, and I forgot this, magic_quotes_gpc is on by default in PHP, which essentially runs addslashes() for you.  This is rather retarded, and should be forced off all the time.

> ot to sound harsh, but you seem to be the smartass of the programming forum. I would say people as smart as you seem to be would spend their time doing something more useful than talking about their smartness.Seeing as my smartness is actually helping people write better and more correct code, I think you need to sod off.

---

### Post by ZylGadis on 2006-02-15
Please take a look at my more extensive post in another thread overtaken by you, and please note that I won't tolerate expressions like the one in your last sentence.

---

### Post by LordHunter317 on 2006-02-15
[QUOTE=Alex.P]please note that I won't tolerate expressions like the one in your last sentence.[/QUOTE]Then you can stop posting, for all I care.  **You** started the personal attacks, not me, and your **whole** post was nothing but a personal attack.

You're hardly blameless here, and what sort of response did you expect?  Flowers and sunshine.  

Had you just said, "Can you please cite your explanation externally," or, "Does anyone else say anything about this," you would have gotten the same answer without the snide remark.  I would have been actually, *pleasant.*.

As I've said on a number of occasions, I can be quite frequently terse, for several reasons.  If you ask for clarification, you'll get all the clarification you want.  No need to attack me for it.

---

### Post by zkissane on 2006-02-15
[QUOTE=LordHunter317]PHP itself ships two MySQL drivers: Mysql, which uses the mysql_* family of functions, and mysqli which is a class that performs similar functionality.  You should use always use mysqli over mysql.  Both are documented on php.net.
[/QUOTE]

Is there a way to get the mysqli driver to work with apt packages?  I've installed the "typical" (I guess) php5, mysql, and apache2 packages, but PHP tells me that mysqli isn't a defined class.  I read php.net's page on it and it seems that the only way to get it to work is to make PHP from source.  Or am I doing something stupid like forgetting to include a file in my PHP code?

---

### Post by LordHunter317 on 2006-02-15
[QUOTE=zkissane]Is there a way to get the mysqli driver to work with apt packages?  I've installed the "typical" (I guess) php5, mysql, and apache2 packages, but PHP tells me that mysqli isn't a defined class.  I read php.net's page on it and it seems that the only way to get it to work is to make PHP from source.  Or am I doing something stupid like forgetting to include a file in my PHP code?[/QUOTE]Mysqli isn't currently package in Debian or Ubuntu AFAICT, though there have been requests to do so.

I believe you can find packages that might work at dotdeb.org.  Obviously, if you use them and they break stuff, you keep all the pieces ;)

ADODB and PEAR::DB are packaged however.

---

### Post by dudus on 2006-04-10
Do you guys mean that the rigth way to do the qute thing is to disable magic_quotes, forget about "mysql" and stick with either "mysqli" ADODB OR PEAR:DB?

If I just use any of these classes for my queryes I can be safe against mysql injections?

---

