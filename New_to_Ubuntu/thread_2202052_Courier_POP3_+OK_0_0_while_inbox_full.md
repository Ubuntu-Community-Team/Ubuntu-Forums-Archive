---
title: "Courier POP3 +OK 0 0 while inbox full"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by casper5 on 2014-01-27
I'm having the following problem: I want to see if I got new email and retrieve that new email, however my Courier POP3 server returns +OK 0 0 on a STAT command.
These are my logs:

Raw connection:
```
Trying 192.168.1.40...
Connected to mail.hostname.nl.
Escape character is '^]'.
+OK Hello there.
user casper
+OK Password required.
pass ********
+OK logged in.
stat
+OK 0 0

```

mail.log
```
Jan 27 11:16:15 hostname pop3d: LOGIN, user=casper, ip=[::ffff:192.168.1.6], port=[51174]Jan 27 11:16:22 hostname postfix/pickup[4977]: 6118D6A52: uid=1001 from=<casper>
Jan 27 11:16:22 hostname postfix/cleanup[5511]: 6118D6A52: message-id=<20140127111622.6118D6A52@smtp.hostname.com>
Jan 27 11:16:22 hostname postfix/qmgr[4978]: 6118D6A52: from=<casper@hostname.com>, size=415, nrcpt=1 (queue active)
Jan 27 11:16:22 hostname postfix/local[5513]: 6118D6A52: to=<root@hostname.com>, orig_to=<root>, relay=local, delay=0.08, delays=0.05/0/0/0.03, dsn=2.0.0, status=sent (delivered to mailbox)
Jan 27 11:16:22 hostname postfix/qmgr[4978]: 6118D6A52: removed
Jan 27 11:16:29 hostname pop3d: LOGOUT, user=casper, ip=[::ffff:192.168.1.6], port=[51174], top=0, retr=0, rcvd=20, sent=62, time=14

```
mail command:
```
casper@hostname:/var/log$ mail"/var/mail/casper": 4 messages 4 unread
>U   1 root@hostname.nl    Mon Jan 27 10:14  18/442   
 U   2 Casper      Mon Jan 27 10:19  19/622   test
 U   3 C           Mon Jan 27 10:20  43/1924  Hi!
 U   4 C           Mon Jan 27 10:48  43/1916  test
? logout
Unknown command: logout
? quit
Held 4 messages in /var/mail/casper
```

Can someone explain why STAT returns +OK 0 0 while there are 4 unread messages in my inbox?

EDIT: I found that the Maildir does not contain any messages (the structure is there however).
How can I get my POP3 point to the right location of my messages?

---

### Post by casper5 on 2014-01-27
Finally got it working by removing Courier POP3 and Courier IMAP and doing the install again according: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

