---
title: "[SOLVED] Evolution 2.22.2 Need to set SMTP Port"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by enderal on 2008-08-28
[SIZE="3"]I know that I need to use port 587 through my wireless Internet Provider to send SMTP email but this Evolution 2.22.2 does not seem to have a way to set it up like all the other email clients I have ever used.

Is there a way?

Thank you.[/SIZE]

---

### Post by cariboo on 2008-08-29
I got this from this page here:

[http://onlyubuntu.blogspot.com/2008/06/howto-configure-evolution-to-work-with.html](http://onlyubuntu.blogspot.com/2008/06/howto-configure-evolution-to-work-with.html)

to setup the correct port:

> 1. Open Evolution and click EDIT -> PREFERENCES from the menu.

2. On the left, ensure MAIL ACCOUNTS is high-lighted. Click ADD.

3. Click FORWARD.

then for smtp server setup:

> Now add the following for SENDING EMAIL (heading at top of the window)

Server Type: SMTP

SERVER: plus.smtp.mail.yahoo.com:465 (Notice port number at the end)

Server requires authentication: Check this box

Use Secure Connection: SSL Encryption

Authentication: Plain

Username: your username WITHOUT the @yahoo.com

For server change it to your servers and add the port at the end of the string as above.

Jim

---

### Post by enderal on 2008-08-29
That works.

Thanks!

---

