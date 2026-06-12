---
title: "[SOLVED] SquirellMail: Can not login (imapd?)."
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Freyja on 2008-06-05
Hello together.

Recently I tried to set up a mail server based postfix with Ubuntu.
Unfortunately I got stuck at the testing with SquirellMail.
Guess there is a problem with the MySQL-User (look at the log file at the end) but I can not figure it out.

Since I do not know what data you need (this is my second day using Ubuntu) for helping me I just added all variable stuff.


Guide I used:```

 - http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04
```

System:```

 - Ubuntu
 -> Release 8.04 (hardy)
 -> Kernel Linux 2.6.24-18-server
 -> GNOME 2.22.2
```

MySQL:```

 - domains(domain): lain.ch
 - users(email, password, quota): root@lain.ch, *******, 10485760
```

netstat -tap | grep mysql:```

 - tcp        0      0 localhost:mysql         *:*             LISTEN      11934/mysqld
 -> Guess this is fine.
```

/etc/pam.d/smtp:```

 - auth    required   pam_mysql.so user=lainSQL passwd=aPassword host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1
 - account sufficient pam_mysql.so user=lainSQL passwd=aPassword host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1
```

/etc/postfix/sasl/smtpd.conf:```

 - pwcheck_method: saslauthd
 - mech_list: plain login
 - allow_plaintext: true
 - auxprop_plugin: mysql
 - sql_hostnames: 127.0.0.1
 - sql_user: aUsername
 - sql_passwd: aPassword
 - sql_database: mail
 - sql_select: select password from users where email = '%u'
```

/etc/courier/authmysqlrc:```

 - MYSQL_SERVER localhost
 - MYSQL_USERNAME aUsername
 - MYSQL_PASSWORD aPassword
 - MYSQL_PORT 0
 - MYSQL_DATABASE mail
 - MYSQL_USER_TABLE users
 - MYSQL_CRYPT_PWFIELD password
 - #MYSQL_CLEAR_PWFIELD password
 - MYSQL_UID_FIELD 5000
 - MYSQL_GID_FIELD 5000
 - MYSQL_LOGIN_FIELD email
 - MYSQL_HOME_FIELD "/home/vmail"
 - MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
 - MYSQL_QUOTA_FIELD quota
```

telnet localhost pop3:```

 - Trying 127.0.0.1...
 - Connected to localhost.
 - Escape character is '^]'.
 - +OK Hello there.
```

netstat -tap:```

 - Active Internet connections (servers and established)
 - Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
 - tcp        0      0 localhost:10024         *:*                     LISTEN      10487/amavisd (mast
 - tcp        0      0 localhost:10025         *:*                     LISTEN      11789/master    
 - tcp        0      0 localhost:mysql         *:*                     LISTEN      11934/mysqld    
 - tcp        0      0 *:www                   *:*                     LISTEN      8031/apache2    
 - tcp        0      0 .....local:domain   *:*                     LISTEN      5050/named      
 - tcp        0      0 localhost:domain        *:*                     LISTEN      5050/named      
 - tcp        0      0 localhost:ipp           *:*                     LISTEN      5834/cupsd      
 - tcp        0      0 *:smtp                  *:*                     LISTEN      11789/master    
 - tcp        0      0 localhost:953           *:*                     LISTEN      5050/named      
 - tcp        0      0 localhost:37374         localhost:pop3          TIME_WAIT   -               
 - tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      11818/couriertcpd
 - tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      10363/couriertcpd
 - tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      10322/couriertcpd
 - tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      11836/couriertcpd
 - tcp6       0      0 [::]:domain             [::]:*                  LISTEN      5050/named      
 - tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      9921/sshd       
 - tcp6       0      0 ip6-localhost:953       [::]:*                  LISTEN      5050/named      
 - tcp6       0      0 localhost:pop3          localhost:37375         TIME_WAIT   -   
```

telnet localhost 25:```

 - Trying 127.0.0.1...
 - Connected to localhost.
 - Escape character is '^]'.
 -> ehlo localhost:
 ->> 220 ..... ESMTP Postfix (Ubuntu)
 ->> 250-.....
 ->> 250-PIPELINING
 ->> 250-SIZE 10240000
 ->> 250-VRFY
 ->> 250-ETRN
 ->> 250-STARTTLS
 ->> 250-AUTH LOGIN PLAIN
 ->> 250-AUTH=LOGIN PLAIN
 ->> 250-ENHANCEDSTATUSCODES
 ->> 250-8BITMIME
 ->> 250 DSN
 ->>> Guess this is alright too.
```

mailx aUsername:```

 - Well get no output here, guess it worked.
 -> Can I check this?
 ->> Jun  5 19:37:55 ..... postfix/pickup[13214]: E31E25E034D: uid=0 from=<...>
 ->> Jun  5 19:37:55 ..... postfix/cleanup[13216]: E31E25E034D: message-id=<20080605173755.E31E25E034D@.......>
 ->> Jun  5 19:37:55 ..... postfix/qmgr[13215]: E31E25E034D: from=<....>, size=309, nrcpt=1 (queue active)
```

[color=red]http://localhost/squirrelmail/src/login.php:[/color]```

 - aUsername/aPassword
 -> ERROR: Connection dropped by IMAP server.
```

[color=red]mail.log:[/color]```

 - ....
 - Jun  5 19:40:15 ..... authdaemond: failed to connect to mysql server (server=localhost, userid=lainSQL): Access denied for user 'lainSQL'@'localhost' (using password: YES)
 - Jun  5 19:40:15 ..... imapd: LOGIN FAILED, user=root@lain.ch, ip=[::ffff:127.0.0.1]
 - Jun  5 19:40:15 ..... imapd: authentication error: Input/output error
 ->> I can login with this manually: mysql -u lainSQL -p
 - ....
```

Tried already:```

 - Repeated the guide a few times.
 - Various pages do not remember all.
 - Read FAQ and help files the whole day now but still am at the same point.
```

Thank you for your help and time

---

### Post by ZabiGG on 2008-06-05
Here is the link to the SquirellMail developer's site, if it helps...

[http://www.squirrelmail.org/](http://www.squirrelmail.org/)

Cheers,

Z.

---

### Post by Freyja on 2008-06-06
> **ZabiGG said:**
> Here is the link to the SquirellMail developer's site, if it helps...

[http://www.squirrelmail.org/](http://www.squirrelmail.org/)

Cheers,

Z.

Well to be honest, I was reading that bug report before, so nothing new there, but thank you anyway
So I repeated that guide two more times and it works now finally, but I can not tell what was wrong.

I got a completely different question, may I post this here or am I to create a new thread?

---

### Post by ZabiGG on 2008-06-06
You should mark this one solved (click on the link in my signature if you need to learn how), and start a new thread with your new question.

Cheers,

Z.

---

