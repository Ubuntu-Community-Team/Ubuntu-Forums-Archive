---
title: "Problems installing LAMP"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by Rebecca_D on 2014-09-21
I have been trying, on a number of ocassions, to install LAMP (Apache, MySql, PHP) on 14.04 Trusty.

After trying to complete installation by running > mysql_installation_securethe process asks, as you may already know, for the password of > root@localhost
I tried what I thought was the root password, the account password for my administrative account and even blank, but nothing seemed to work. I then resorted to resetting the root password using > sudo passwrd root but the use of the new password did not work either. Really frustrating.

Where I am going wrong? Any help would be gratefully received. Thanks.

---

### Post by SeijiSensei on 2014-09-21
The root account and password in MySQL has no relation to the root account in Linux.  I suggest you start by reading this section of the MySQL manual: [http://dev.mysql.com/doc/refman/5.5/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.5/en/default-privileges.html)

---

### Post by Rebecca_D on 2014-09-21
Thank you for your reply SeijiSensei. You're answer however does not help me. Perhaps I have not explained myself precisely. The problem arises when I run mysql_secure_installation after the installation of mysql has completed. The immediate output from this instruction is: > NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):  This is where I find that I cannot what I believe is the root password. You seem to imply that I do not need it. I have also just tried hitting enter as suggested but without success.

For information, as someone who is still learning the Linux environment, I was following the instructions for installing LAMP given here [http://tinyurl.com/nvqf434]("http://tinyurl.com/nvqf434")

---

### Post by yancek on 2014-09-22
It is explained in detail on that page if you scroll down to the section "Assigning root account Passwords", make sure you use the Unix method.  And initially, there is no password and anyone who access the machine could do anything in mysql which is why it is a good idea to set a root password.  Also, it is not related to your root password for the operating system although you could use the same password if you wish.

Also, using sudo passwrd root would be used to change the operating system root password, not mysql.  I assume that is a type and you actually typed passwd?

What you should have done in a terminal is type:  
[B]mysql -u root

You should then have got a mysql prompt:  mysql>
From there you would type:  [/B][B][B]SET PASSWORD FOR 'root'@'localhost' = PASSWORD('*newpwd*');

You need to have exactly like the above except to change newpwd to whatever your actual password is.
[/B][/B]

---

### Post by steeldriver on 2014-09-22
Do you actually remember setting the mysql root password to be the same as that of your administrative account?

If it was a completely new mysql-server install, then you should have been presented with a dialog to set the root password. However if mysql-server was previously installed, it would have skipped that step (and used the existing user table). In the latter case, you should be able to set/reset the root password by reconfiguring the package, e.g.

```

sudo dpkg-reconfigure mysql-server-5.5

```

(change the 5.5 if your version is different).

---

### Post by Rebecca_D on 2014-09-22
Thanks to **Yancek** and **steeldriver** for their replies.

**Yancek**. Your method did not work for me. Output was> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
**steeldriver**. Your method worked and I now have been able to secure MySql.

---

### Post by yancek on 2014-09-22
> **Yancek**. Your method did not work for me. Output was 	 		 			

It wasn't "my" method but the method explained by the developers of mysql.  The other method you used was basically reconfiguring the entire installation.  I'd suggest you bookmark the link posted above to mysql.

---

### Post by Rebecca_D on 2014-09-22
I'm sorry if I have offended you Yancek, it was not my intention. When saying "your method", I did not know that you were quoting it from elsewhere. Perhaps I should have said "your suggestion". However as a newbie to Apache, MySql & PHP I would hope that more experienced users would be able to understand such faut pas.

---

### Post by yancek on 2014-09-22
I was referring to the link posted below which I though was linked to by another member but I don't see it.   Maybe I just forgot to post the link.  The second link below is to the mysql documentation page which is very detailed although it is a little cryptic at times.  Good luck with it.
[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

[http://dev.mysql.com/doc/refman/5.7/en/index.html](http://dev.mysql.com/doc/refman/5.7/en/index.html)

---

