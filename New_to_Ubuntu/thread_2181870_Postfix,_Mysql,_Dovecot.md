---
title: "Postfix, Mysql, Dovecot"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by sunveer on 2013-10-19
I have postfix, mysql and dovecot on three different machines.  How can I connect postfix to mysql (for virtual users) and postfix to dovecot (for storing emails)?

---

### Post by SeijiSensei on 2013-10-19
For postfix+dovecot, you could export the mail folders from the dovecot machine with NFS and mount them on the Postfix machine.  However I would strongly suggest putting dovecot on the same machine as Postfix.  The only other solution is to run a separate instance of Postfix on the dovecot machine and configure your current Postfix machine to relay all its mail to the Postfix instance running on the dovecot machine.

For MySQL, you can tell Postfix to [talk to the other machine]("http://www.postfix.org/mysql_table.5.html") over the network.  You would need to configure the MySQL server to listen on its network interface as well as 127.0.0.1.  I suspect a similar method would be used to communicate between dovecot and MySQL.

Frankly, though, this seems like a lot more trouble than simply installing all three services on one machine.

---

