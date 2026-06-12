---
title: "Commands for Postfix mail server"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by Bob_OHara on 2014-09-11
Looking for 2 command lines:

1) A way to check the spool - this would only be used to see if email is backing due to a compromised email account or mail delivery issue

2) A way to check mail server logs for rejected email on a certain date.

We are just now implementing Zpanel on Ubuntu and using Roundcube for the web mail interface. Need this info to watch for issues during the initial phases of moving customer email accounts over and in the future if one should call with mail delivery issues
Bob - USA Choice

---

### Post by Bob_OHara on 2014-09-11
Figured this out pretty much but still in search of a way to actually search the deferred mail by date or email address. For example if a customer of ours calls and says their missing an email from so and so on a certain date

---

### Post by JKyleOKC on 2014-09-11
Have you looked at "man postqueue" yet? It can show you all deferred mail that's still in a queue. The actual logs may well be rotated on a daily basis, and also may not retain the old ones for more than four days -- which may be too short a time for users to complain. You can set "logrotate" up to retain old logs for as many days as you like, so this bears investigation also.

---

### Post by nerdtron on 2014-09-11
1. "mailq" to see the queue of the emails and "sudo qshape" to see a table like output on how many emails on each domain the email is sending.

2. You need to edit the /etc/postfix/main.cf file to add/remove/edit some few config lines. See [http://www.linuxtopia.org/online_books/mail_systems/postfix_documentation/TUNING_README_008.html](http://www.linuxtopia.org/online_books/mail_systems/postfix_documentation/TUNING_README_008.html)

---

