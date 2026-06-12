---
title: "Run phpunit from any folder"
date: 2012-04-10
forum: Programming Talk
---

### Post by retrodans on 2012-04-10
I am trying to get phpunit_selenium working, but am having some trouble with the PHPUnit pear installation.  It is installed, and when I run phpunit from /usr/share/php it works fine.  But ideally I would run this command from anywhere on my machine.

This sounds like a very beginner question, but it would be very useful to know how to get this setup.  Do I need to modify .bashrc with a new alias or something similar?

Thanks for the advice.

Dan

---

### Post by generic41209 on 2012-04-15
search engine:
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables)

---

### Post by retrodans on 2012-04-16
Thanks for the informative link, but sadly it didn't seem to work.  The steps I took were:


1.
Change PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
TO: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/share/php"
in /etc/environment

2.
Reboot

3. run 'phpunit', hoping for the help information (as that is what I receive if I cd into usr/share/php and run phpunit from there)


Is there a step I potentially missed in changing this file.  Myunderstanding from readin the introduction to that page was that PATH is used to try running the function before it fails, to see if it works in any of them.  So in theory it would try my php/phpunit folder.  I don't know if it's worth finding where the 'phpunit' variable is setup for /usr/share as there is no environment variable file in there that I can see.

Thanks again for your advice.

---

