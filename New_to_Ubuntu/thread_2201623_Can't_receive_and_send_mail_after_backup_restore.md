---
title: "Can't receive and send mail after backup restore"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by roy5 on 2014-01-25
Hi,

Yesterday i restored 2 different backups on 2 individual VPS servers.
My hoster made those backups daily, but now i got a problem with both of my servers
For some reason, my mail is down. I cant receive or send any mail.

My log files server #1

```
Jan 25 12:16:10 h1939728 postfix/trivial-rewrite[31748]: fatal: open database /var/spool/postfix/plesk/transport.db: Invalid argumentJan 25 12:16:11 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/trivial-rewrite pid 31748 exit status 1
Jan 25 12:16:11 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jan 25 12:16:24 h1939728 postfix/smtpd[31749]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:16:25 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/smtpd pid 31749 exit status 1
Jan 25 12:16:25 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 25 12:17:11 h1939728 postfix/trivial-rewrite[31751]: fatal: open database /var/spool/postfix/plesk/transport.db: Invalid argument
Jan 25 12:17:12 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/trivial-rewrite pid 31751 exit status 1
Jan 25 12:17:12 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jan 25 12:17:25 h1939728 postfix/smtpd[31752]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:17:26 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/smtpd pid 31752 exit status 1
Jan 25 12:17:26 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 25 12:18:12 h1939728 postfix/trivial-rewrite[31757]: fatal: open database /var/spool/postfix/plesk/transport.db: Invalid argument
Jan 25 12:18:13 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/trivial-rewrite pid 31757 exit status 1
Jan 25 12:18:13 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jan 25 12:18:26 h1939728 pop3d: IMAP connect from @ [::ffff:207.46.8.222]INFO: LOGIN, user=johan@domain.nl, ip=[::ffff:207.46.8.222]
Jan 25 12:18:26 h1939728 postfix/smtpd[31760]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:18:27 h1939728 pop3d: 1390648707.677664 LOGOUT, user=johan@domain.nl, ip=[::ffff:207.46.8.222], top=0, retr=0, time=1, rcvd=24, sent=3887, maildir=/var/qmail/mailnames/domain.nl/johan/Maildir
Jan 25 12:18:27 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/smtpd pid 31760 exit status 1
Jan 25 12:18:27 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 25 12:19:13 h1939728 postfix/trivial-rewrite[31764]: fatal: open database /var/spool/postfix/plesk/transport.db: Invalid argument
Jan 25 12:19:14 h1939728 postfix/master[29033]: warning: process /usr/lib/postfix/trivial-rewrite pid 31764 exit status 1
Jan 25 12:19:14 h1939728 postfix/master[29033]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
```

Server #2 

```
Jan 25 12:01:51 h1900772 imapd: IMAP connect from @ [::ffff:37.153.233.122]INFO: LOGIN, user=research@domain.nl, ip=[::ffff:37.153.233.122], protocol=IMAPJan 25 12:01:51 h1900772 imapd-ssl: IMAP connect from @ [::ffff:37.153.233.122]INFO: LOGIN, user=info@thuiswinkelen.in, ip=[::ffff:37.153.233.122], protocol=IMAP
Jan 25 12:01:51 h1900772 pop3d: IMAP connect from @ [::ffff:37.153.233.122]ERR: 1390647711.984728 LOGOUT, user=roy@domain.nl, ip=[::ffff:37.153.233.122], top=0, retr=0, time=1, rcvd=24, sent=75068, maildir=/var/qmail/mailnames/domain.nl/roy/Maildir
Jan 25 12:01:55 h1900772 pop3d: LOGIN FAILED, ip=[::ffff:37.153.233.122]
Jan 25 12:02:09 h1900772 postfix/smtpd[1351]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:02:10 h1900772 postfix/master[861]: warning: process /usr/lib/postfix/smtpd pid 1351 exit status 1
Jan 25 12:02:10 h1900772 postfix/master[861]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 25 12:02:22 h1900772 postfix/smtpd[1354]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:02:23 h1900772 postfix/master[861]: warning: process /usr/lib/postfix/smtpd pid 1354 exit status 1
Jan 25 12:02:23 h1900772 postfix/master[861]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 25 12:03:10 h1900772 postfix/smtpd[1420]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:03:11 h1900772 postfix/master[861]: warning: process /usr/lib/postfix/smtpd pid 1420 exit status 1
Jan 25 12:03:11 h1900772 postfix/master[861]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 25 12:03:23 h1900772 postfix/smtpd[1421]: fatal: open database /var/spool/postfix/plesk/blacklists.db: Invalid argument
Jan 25 12:03:24 h1900772 postfix/master[861]: warning: process /usr/lib/postfix/smtpd pid 1421 exit status 1
Jan 25 12:03:24 h1900772 postfix/master[861]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

After the backup on server #1 i also had this issue with my innodb: [http://stackoverflow.com/questions/21333843/unknown-table-engine-innodb-after-backup](http://stackoverflow.com/questions/21333843/unknown-table-engine-innodb-after-backup). This problem is fixed, but maybe it has something to do with this issue?

My hoster said that the problems has to do with my own configuration. But I think thats strange, because on the date when those backups are made everything worked correctly... What do you think? 

Please, help me.

---

### Post by roy5 on 2014-01-25
Found the solution on this post: [http://forum.parallels.com/showthread.php?101696-fatal-open-database-var-spool-postfix-plesk-poplock-db-Invalid-argument](http://forum.parallels.com/showthread.php?101696-fatal-open-database-var-spool-postfix-plesk-poplock-db-Invalid-argument) with some help from a friend.

---

