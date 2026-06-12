---
title: "Ubuntu upgrade bug"
date: 2017-05-25
forum: New to Ubuntu
---

### Post by rvdesai on 2017-05-25
[COLOR=#333333][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I am upgrading ubuntu 14.04 to 16.04.. I am getting errror 2002. I am attaching screenshot for that. I check /var/run/mysql/mysqld.sock file. It is empty. Do you have any idea to solve this error?
[/FONT][/COLOR][ATTACH=CONFIG]275296[/ATTACH][ATTACH=CONFIG]275297[/ATTACH]

---

### Post by ian-weisser on 2017-05-25
The error message seems very clear about what the problem is, and the error message provides several ways to resolve the problem.

Are you asking because you did not read the error message?
Or you do not understand the error message?
Or you need help applying one of the solutions? (which one?)
Or you tried all the solutions, and none worked? (what were the resulting errors?)

---

### Post by rvdesai on 2017-05-25
Hello,
I am new to ubuntu. I am learning ubuntu for upgrading moodle server. Rightnow our moodle server is on ubuntu 14.04..and I am trying to upgrade to 16.04

mysql 5.5.53
php 5.5.9
apache 2.4.7

However, I am getting an error during the upgrade.

I also did a research for mysqld.sock file and it is for transmission of data. It supposed to be empty. 

The other try I did was


[COLOR=#242729][FONT=Arial]Edit the file /etc/dbconfig-common/phpmyadmin.conf, changing[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]dbc_dbport='' to dbc_dbport='0'[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After edit the file and save it,  and ran sudo dpkg-reconfigure phpmyadmin (choose **Yes** when ask you if you want to Reinstall database for phpmyadmin).

It didn't work for me. And now I don't know how to deal with this situation....

I am trying to solve this error for 2 days....still didn't get any solution for that..

I really want to understand the meaning of this error and also the right solution for that...

I don't know which solution would be right. However, I also did some research and seems like it is a ubuntu bug


Please give me some steps to deal with this error.

I also tried to ignore this error and when I ignore. I can upgrade successfully.

However, ignoring the error on production environment is not an good solution to choose.

I did every try to solve this error...However, I couldn't fix this error.


Thanks[/FONT][/COLOR]

---

### Post by ian-weisser on 2017-05-25
If you select RETRY, are you able to add port 3306?

---

### Post by rvdesai on 2017-05-26
Where do I need to add the port? I am not seeing any option to add a port..

Thanks

---

