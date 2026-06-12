---
title: "MySql installation/first use errors"
date: 2017-09-03
forum: New to Ubuntu
---

### Post by messydrew on 2017-09-03
[SIZE=2][FONT=arial]I'm attempting to install MySql along with the Workbench so that I can begin using the SQL commands that I've recently learned to create my first database. I followed MySql's installation instructions for both, using apt-get. When I tried making a new connection in workbench, I got the error "[/FONT][/SIZE]Access Denied for User 'root'@'localhost'." Thinking this may be caused by the fact that I do not log in as root, I granted my user all sudo permissions. No change sent me looking into forums and MySql documentation, where I found directions to use the following commands:
     ```
$ sudo mysqladmin shutdown
$ [COLOR=#0077AA][FONT=&amp]chown [/FONT][/COLOR][COLOR=#990055][FONT=&amp]-R [/FONT][/COLOR]*user_name **/path/to/mysql/datadir*
```
The first command worked without error, but when trying to find the path for datadir, I discovered that it doesn't exist on my computer. According to the documentation, it should have been included in the install. I've been searching for hours, and I don't want to try too many more fixes (besides these errors there were some I was able to correct or get around) because I don't know enough about Ubuntu yet to be sure I'm not going to delete or move necessary files.

Any help would be greatly appreciated.

---

### Post by cariboo on 2017-09-03
When installing Mysql, you should have been prompted to create a password for the root user of Mysql. This does not create a system-wide root user.

For help, have a look here:

[https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords](https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords)

---

### Post by SeijiSensei on 2017-09-04
MySQL stores all its data in /var/lib/mysql, and all files are owned by the "mysql" system account.  You don't want to touch any of that.

---

