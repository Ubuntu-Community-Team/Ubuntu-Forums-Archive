---
title: "Mailserver Redundancy - Client side"
date: 2015-03-01
forum: New to Ubuntu
---

### Post by Dominic--- on 2015-03-01
Hi,

I hope someone here can show me some insight on the following.

I want to setup a redundancy for my mail server (two physical separate servers)
Now I understand I need to add a MX record for the backup mailserver.
But what I don't understand is how mail clients know how to contact which mailserver.

For example, if mail01 is down, how does any mail-client know to contact mail02?
Do mail-clients actually use MX records for this (always thought they solely rely on DNS)?

Best regards,

Dominic

---

### Post by lisati on 2015-03-01
Yes, it's possible to have DNS set to indicate that you have multiple servers, but how easy this is to achieve can depend on your DNS hosting provider. The last time I used a free service such as no-ip, I only ever saw a place to record details for one MX server. 

 The MX record has a priority field with it: the lower the number, the higher the priority.

---

### Post by Dominic--- on 2015-03-01
I can change the MX records in a few seconds, so no problems there :)
So basically, if I add another MX record, with a higher number (thus lower priority), and the connection to the first server fails, clients will try to connect to the second server, based on the MX records?

---

