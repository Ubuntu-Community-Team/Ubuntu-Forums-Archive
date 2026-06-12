---
title: "mysql login problem"
date: 2009-04-16
forum: Programming Talk
---

### Post by macdonald on 2009-04-16
I have installed mysql in linux 8.10 desktop. I have also installed phpmyadmin. There only one user in mysql 'root'. I can login root from localhost/phpmyadmin but I don't know how to login from the terminal.

More suggestions to make the working easy will be appreciated. 

Please also tell me a good IDE for writing C++ programs.

---

### Post by hobbestec on 2009-04-16
mysql -u root -p

the -u specifies the username

-p makes it prompt for your password

Then you will get to the mysql prompt, which certianly is not as nice as using phpmyadmin for most things.  I usually just use phpmyadmin for everything.

---

### Post by Sunon on 2009-04-16
I really like komodo, but netbeans is also popular

---

### Post by macdonald on 2009-04-17
@hobbestec
Thanks a lot. It worked. I typed :
mysql -u root -padmin
and it prompted for the password. But I never gave the user name. Why is it so.
I will also use phpmyadmin, I just wanted to try my hands mysql prompt. One should have the basic knowledge, in case phpmyadmin fails.
Please suggest a website where I can find this info about connecting to a database, displaying the tables it has, viewing the tables etc. I want just an introduction.
Thanks once again.

---

