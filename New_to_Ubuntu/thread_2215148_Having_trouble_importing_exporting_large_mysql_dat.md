---
title: "Having trouble importing exporting large mysql database"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by sskrnguy on 2014-04-05
hey guys. newbie member here. i need some help. 

im trying to move the entire linux server on the web to my own linux server. (im very new at this) . i have managed to save all the files from the web to each directory. i now need to, export and import mysql database but  the size is nearly 600mb so i could NOT do this over phpmyadmin. upon searching the web, i found command mysqldump for export and have managed to save the sql file onto my root folder.   Now the problem is... ive tried to upload this sql file to my new server using FTP but it keeps getting cut off at 500mb. i have also tried using the program WINSCP but its giving me the same problem (cuts off at 500mb).  
does anybody know why this is happening? please help
thanx

---

### Post by gopukrishnan on 2014-04-05
Hi,

I am not sure why it breaks atlast. You may check the logs first. Regarding mysql, try to restore from one machine to the other without moving the dump. Hope the below link help you.
[http://gopukrish.wordpress.com/2013/08/14/take-and-restore-mysql-backup-from-localmachine-to-a-remote-machine/](http://gopukrish.wordpress.com/2013/08/14/take-and-restore-mysql-backup-from-localmachine-to-a-remote-machine/)

---

### Post by sskrnguy on 2014-04-05
thanx for the reply.  this is awesome. do all in one shot. 
[B]
mysqldump -u *user_name* -p *password* *db_name *| mysql -u *username *-p *password* &#8211;host=*host_IP* -C [I]db_name
[/I][/B]
so for example, it should looks like this? 

mysqldump -u testuser -p 1234 mydata | mysql -u testuser -p 1234 -host=host_192.168.1.2 mydata? 

thanx

---

### Post by SeijiSensei on 2014-04-05
Alternatively you could just compress the file with gzip and send the compressed version over the wire.  Because dumps are pure text, they compress very highly.

```

$ sudo mysqldump ... > mydumpfile
$ gzip mydumpfile
$ scp mydumpfile.gz me@somewhere:/some/folder

```
Then use gunzip on the file mydumpfile.gz to uncompress.

---

### Post by sskrnguy on 2014-04-07
thank you guys for the help. i've managed to import the entire db. =)   . i have another issue though. im running this server on a virtualbox as a guest.  host being win7.  

when this machine was connected to my router, everything worked fine. no issues.  however, i bought some additional static IPs from my provider (verizon) , so that i can have a specific IP for this web server.  
 
what setting do i need to have the webserver running as open server on the virtualbox? ive tried NAT, HOST ADAPTER, BRIDGED ADAPTER but none of them works. none of them gives a local ip to the server. please help. 
thank you

---

### Post by SeijiSensei on 2014-04-07
Partly this is a routing question.  How are you implementing these additional addresses?  Is Verizon managing your router?

This question deserves a separate thread.

---

### Post by sskrnguy on 2014-04-07
> **SeijiSensei said:**
> Partly this is a routing question.  How are you implementing these additional addresses?  Is Verizon managing your router?

This question deserves a separate thread.

i have sent you a pm for help if you dont mind. 
thank you

---

