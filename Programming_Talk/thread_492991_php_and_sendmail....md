---
title: "php and sendmail..."
date: 2007-07-05
forum: Programming Talk
---

### Post by tocleora on 2007-07-05
Not sure if this should go in programming or server, so I thought I'd start here.

I have an internal server with no domain name.  I built a ticket system that they want an e-mail sent to their e-mail address (which is on an external server) when someone submits a ticket.  However e-mails aren't making it to the external mail server.  

I should also mention this is a fedora core 4 box.  I'm prepping  a ubuntu box to move to but I did try this on it as well and did not receive the e-mail.

The code I'm using in my php file:

```

mail($mailto, "Testing", "Testing", "From: $mailfrom\nContent-Type: text/plain;charset=iso-8859-1");

```

where mailto is say "name1@domain.com" and mailfrom is "name2@domain.com", domain.com being the external mail server domain.

I use this code frequently so I'm 99% sure it's not this one (I copy and paste).

I went into php.ini and it has this:

```

sendmail_path = /usr/sbin/sendmail -t -i

```

Then I went into webmin sendmail, and added the mail server domain to Relay Domains, I added it in Outgoing Domains, and I added "apache" as a trusted user since it is the account php uses (to my knowledge).

Anything else I'm missing? Is there an alternative way to send this?  I tried doing it via telnet as well (using fsocketopen) but php isn't resolving the smtp mail server domain.  Any other assistance would be greatly appreciated!

---

### Post by leibowitz on 2007-07-05
If it's not a programming issue why did you post it in the programming talk forum ?

you should ask a moderator to move your post, you will get more help.

---

### Post by tocleora on 2007-07-05
Because programmers being the ones using the php mail function might be familiar with this error and may be able to help me...

... and because programmers might be able to assist me an another solution ...

... and as I mention, I didn't know which one it would be better suited in, so I started here ...  I run into programmers not being admins and admins not being programmers either way so I thought I'd start with the people I'm most like ...

Thanks. :)

---

### Post by Mr. C. on 2007-07-05
Which MTA do you have installed ?

What do your maillog messages show?

MrC

---

