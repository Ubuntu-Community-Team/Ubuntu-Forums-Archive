---
title: "MySQL/PHP problem"
date: 2008-07-17
forum: Programming Talk
---

### Post by philo23 on 2008-07-17
Right, well i recently moved my php scripts from my old server to a slightly newer install of ubuntu (8.04) and i did a fresh install of all the standard stuff, php, mysql, lighttpd. how ever inside of php, i cannot connect to the mysql database unless i use the root user. i know i'm not typing something wrong, and i know i've got the passwords right, i also know i have privileges correct, i'm 100% certain of these things, yet all users, apart from root refused to connect via mysqli on this server. i cant login to mysql via the command line fine with any user, i can login to phpMyAdmin fine with any user, but when i try to use any user that isnt root on my php file, it fails with this:
```
Warning: mysqli::mysqli() [function.mysqli-mysqli]: (28000/1045): Access denied for user 'philip'@'localhost' (using password: YES) in /var/www/testdatabase.php on line 2
```
i cant seem to find whats up atal and this is putting a complete halt on all my projects. i dont see whats up with it atal, i've reinstalled ubuntu several times to see if it was just a bug in mysql, with no luck

thanks in advance.

---

### Post by King_Killa on 2008-07-17
Have you installed MySQL Administrator from the Add/Remove Applications screen? Perhaps the secondary account was lost in the transition. I would install it and make sure the account is active and has the correct privileges.

Edit: Oops, missed the part about being able to access the account from phpmyadmin. That does seem exceedingly strange considering phpmyadmin is just a php script. I'd still check out MySQL Administrator to see if there is anything wrong with the account.

---

### Post by philo23 on 2008-07-18
i've installed mysql via the command line as this is simply a server box with no Gnome or KDE or what have you.

i've definitely made the user correctly as i didn't import it from the last one, i actually made one with full privileges. 

Also on a second note, i'd like to say i cant login via the command line mysql ether, it only accepts the root user to login, no one else ether via php, or command line.

---

### Post by kpatz on 2008-07-18
Log into mysql (as root) and issue the command:

```
select host, user from mysql.user;
```

Make sure there is a user philip under localhost.  If there isn't, use this command:

```
grant all on *.* to philip@localhost identified by 'your_password';
```

Then see if your php script works.

---

### Post by philo23 on 2008-07-18
yeah, the user exists and the hosts collum is "%" meaning any host which is correct.

---

### Post by philo23 on 2008-07-18
actually, i just ran your second command. man, thanks. i wonder why thats changed then.... because i never used to have to put localhost in the host field...

thanks any way man, you've saved my life.

---

### Post by kpatz on 2008-07-18
I noticed the same thing after I rebuilt my hardy box (I had an Edgy box that lost a hard drive).  user@% doesn't allow logins from localhost, only user@localhost does.  Maybe it's a new security feature in Mysql or something.

---

### Post by philo23 on 2008-07-18
must be, ether way, thanks man.

---

### Post by |Eric| on 2008-07-19
the command Grants priviledges to the user in question 
its not safe to Grant ALL to a user 
its better to use grant on a specific DB/table 
even better if you use stored procedures as you can limit even further what the user can do & thus give access only to the DB itself (connect to it) & grant access to the procedures only 
(no SQL credentials are needed on the tables accessed by those procedures/functions ) 

you should limit root access to localhost & grant verry limited rights to users ...

there is a somthing_priv or priv_somthing table you can do a select on that table to see what priviledges this or that user has 
there is also a limited amount of privileges in the mysql database in the DB table

---

### Post by philo23 on 2008-07-19
yeah i understand the security problem, and i normally have it setup like you said, i just granted all privs while i tried to figure out what on earth was wrong to see what was up, things are back to how they used to be now.

---

