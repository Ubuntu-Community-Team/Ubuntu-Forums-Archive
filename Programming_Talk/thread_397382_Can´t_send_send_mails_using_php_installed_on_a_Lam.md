---
title: "Can´t send send mails using php installed on a Lamp server over Ubuntu server"
date: 2007-03-30
forum: Programming Talk
---

### Post by albatroz2k on 2007-03-30
I installed a LAMP server, using Xampp over Ubuntu server
everything is fine except for the fact that when I send emails
using the mail php function, it takes a lot and the messages
don´t arrive to hotmail.

I assume that it is because of the fact that I am sending emails
from a non authorized IP, I mean, the IP my messages come from
does not have an email server. BTW I was wonder if it wouldn´t be
better to send my messages through a local email server, available
in the LAN.

What would I need to do so?

---

### Post by Mr. C. on 2007-03-30
PHP uses the "sendmail" binary to post mail to the server to send.  You need a mail server running to relay or forward email.

Do you have postfix, sendmail, or exim installed and configured ?

If so, the "mailq" command will show you messages are queued in the mail spool.

MrC

---

