---
title: "Postfix Status Issue Ubuntu 12.10"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by TRex1780 on 2013-03-23
Hello,

I've been trying to get Postfix reinstalled after removing it previously. I've configured the /etc/postfix/main.cf file, and am looking to run
```
sudo /etc/init.d/postfix reload
```
to apply the changes to main.cf. The following is probably the best way to describe my problem as I can see it:

```
iwmsadmin@iwms:~$ sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration...                                           
postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                         [fail]
user@server:~$ sudo service postfix status
 * postfix is not running
user@server:~$ sudo service postfix start
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
user@server:~$ sudo service postfix status
 * postfix is not running
user@server:~$ sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration...                                           
postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                         [fail]
```

Any ideas? This is my first forum post, so if more information or editing of this post is necessary, please let me know.

---

### Post by Frogs Hair on 2013-03-23
See if there is anything helpful at the link. [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.10)

---

### Post by TRex1780 on 2013-03-23
> **Frogs Hair said:**
> See if there is anything helpful at the link. [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.10)

Hi Frogs Hair,

I don't think I see anything here that helps. The purpose of Postfix on this server is just so that Bugzilla can use it to communicate with users. I don't think many of the installs described in your resource are at all necessary for our needs. Is there maybe a specific section of your resource you have in mind, that I maybe missed?

---

### Post by smtp on 2013-03-26
tail -n 50 /var/log/mail.log

Could you please pate result here?

---

### Post by TRex1780 on 2013-03-26
> **smtp said:**
> tail -n 50 /var/log/mail.log

Could you please pate result here?

Actually the situation has been resolved already, this is the first time I've seen the thread since the issue has been resolved.

For the record, I attempted to install sendmail as an MTA first before using "apt-get remove" to remove sendmail and reinstall postfix. The issue, which was revealed using "ps -ef | grep sendmail" and "ps -ef | grep postfix" is that sendmail was still running on port 25 as the MTA for the server, blocking out Postfix. Issuing "kill" commands to sendmail, then resetting the entire machine resolved the issue.

Thank you for the offer of help, however.

---

