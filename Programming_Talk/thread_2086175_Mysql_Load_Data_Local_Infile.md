---
title: "Mysql Load Data Local Infile"
date: 2012-11-20
forum: Programming Talk
---

### Post by siddharth007 on 2012-11-20
Hi everyone. I want to load the data in text file to a db table.The text  file is located in a remote location(on a linux machine). I am using  this command (inside a bash script on my local system)

**/usr/bin/mysql  -u <username of local machine> -p<password of local  machine> -e "LOAD DATA LOCAL INFILE '//10.X.XX.XX/fileX' INTO TABLE  systime.boottime FIELDS TERMINATED BY ' ' LINES TERMINATED BY '\n';"**

where  10.X.X.XX is the IP address of the remote machine where the text file  is stored (in the location /var/lib/mysql) .However the db table is  located on the local machine and needs to be populated with the text  data in the remote location.I have set the **local-infile=1**  on both local and remote machine as well as the file is stored in the  mysql db directory(which i guess should be readable even remotely). I am  getting this error
[B]
ERROR 1148 (42000) at line 1: The used command is not allowed with this MySQL version[/B]

Any ideas why???

Do i need to provide grants on the remote system or what else??

---

### Post by coldraven on 2012-11-20
What about using scp to copy the file to the local machine and then adding it to your database?
[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

---

### Post by memilanuk on 2012-11-21
Did you try using the Search at the top of every page?

[http://ubuntuforums.org/showthread.php?t=1990780&highlight=mysql+load+data+infile](http://ubuntuforums.org/showthread.php?t=1990780&highlight=mysql+load+data+infile)

---

