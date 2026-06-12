---
title: "How to MySQL in sudoers?"
date: 2009-07-28
forum: Programming Talk
---

### Post by Screatch on 2009-07-28
I am having a small problem adding mysql to sudoers, the reason why i have to do it is because i want the apache and mysql start by click of an icon.

I wrote a small script on bash that would launch apache and mysql at once.. 
In case it helps you it looks something like this.
> #!/bin/bash
service apache2 start
service mysql start
zenity --info --text 'Apache and MySQL has been started sucessfully!'
I am only beginner at bash so point me at any mistakes.

I could handle it via sudo, but the problem is that i don't want to enter the password.
I decided to make modifications via sudoers to add apache and mysql.
This is how it looks now

> # Cmnd alias specification
Cmnd_Alias HTTPD = /etc/init.d/apache2, /var/lib/mysql

# User privilege specification
root    ALL=(ALL) ALL
screatch     ALL=NOPASSWD: HTTPD

It seems to work okay with apache but doesn't with mysql, if i don't use sudo, it ends up with Permission denied.

Please tell me what am i doing wrong.
This should be an easy one but i can't figure what the problem is.

---

### Post by unutbu on 2009-07-28
/var/lib/mysql is the directory that contains the mysql databases.
The mysql script referenced by "service mysql start" is /etc/init.d/mysql

So perhaps try changing
```
Cmnd_Alias HTTPD = /etc/init.d/apache2, /var/lib/mysql
```
to
```
Cmnd_Alias HTTPD = /etc/init.d/apache2, /etc/init.d/mysql
```

---

