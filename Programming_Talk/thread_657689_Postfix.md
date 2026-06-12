---
title: "Postfix"
date: 2008-01-03
forum: Programming Talk
---

### Post by hockey97 on 2008-01-03
HI I am having troubles with postfix.

I am using mysql that's what postfix get's it's postmaps ect.

mainly right now I am failing on lookup tables.

I don't know what mysql need in it's tables to be able to lookup the user e-mail address.

how can I check what postifx see's  as a user's e-mail address .

how can I really figure out what postfix see's or replys to what user and it's e-mail address.

---

### Post by hockey97 on 2008-01-04
I got my mail server up and running . but I only can recieve mail not send it.

also how can I config postfix to send the mail to mysql database.

I have a mysql database that tells postfix  the maildir area.

but postif is not sending the mail to that maildir area it's sending to /var/mail/user
even thought I specified it to send it in the /home/user/domainname/user

and havent seen mail at the maildir I specified.

how can just automaticly make postfix to send the mail to mysql database with the e-mail and the user's e-mail address so I can use php to display e-mails in my website.

and do I need a certificate to send e-mail to like aol and other well-known e-mail service providers??

becuse I tested aol and I can't I got refused.

---

### Post by hockey97 on 2008-01-05
I got this error :  550 5.1.1 : Recipient address rejected: User unknown in virtual alias table  

is this the wrong place to post this?

I really need help  to config postfix so I can send e-mails to mysql and store them in the database rather than a File.

and need to have postfix configured to be able to respond and find the user and user maildir.

---

