---
title: "How to set up Evolution?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-09-15
New to Ubuntu.  Been using Mozilla for my gmail accounts, want to set up Evolution.  Google suggests using IMAP synchronization.  On the Evolution setup assistant I select IMAP and then evolution wants to know the Server, User Name, Security (Use Secure Connection), and Authentication Type (password box, and then box "check for supported types").

What do I put in these boxes?  For example, what does Evolution want in the Server box?  An ISP address like 123.123.123.123?

I am clueless.  Thanks in advance.

---

### Post by howefield on 2008-09-15
receiving mail server name is imap.gmail.com and security is SSL Encryption.
Authentication is PLAIN and I'd hope that you already know your username and password ;)

Post again is you need more.

---

### Post by Therion on 2008-09-15
What kind of email account are you going to be using?  Do you have, for example, a Yahoo! account, or Gmail... Or is it an account provided by your Internet Service Provider?  

Once we know that, we can help you set up the configuration in Evolution.

---

### Post by Mornedhel on 2008-09-15
In your GMail account : Settings (top-right corner), Forwarding and POP/IMAP, IMAP Access > Configuration Instructions, Mail Clients > Other

---

### Post by Thelasko on 2008-09-15
> What do I put in these boxes? For example, what does Evolution want in the Server box? An ISP address like 123.123.123.123?


It's called an IP address and no, it doesn't want that.  What it wants can be found [here.]("http://mail.google.com/support/bin/answer.py?hl=en&answer=13287")

Incoming Mail (POP3) Server -  	pop.gmail.com
[INDENT][INDENT][INDENT]Use SSL: Yes[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]Port: 995[/INDENT][/INDENT][/INDENT]
Outgoing Mail (SMTP) Server -  	smtp.gmail.com (use authentication)
[INDENT][INDENT][INDENT]Use Authentication: Yes[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]Use STARTTLS: Yes (some clients call this SSL)[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]Port: 465 or 587[/INDENT][/INDENT][/INDENT]
Account Name: 	your full email address (including @gmail.com or @your_domain.com)
Email Address: 	your email address (username@gmail.com or [email]username@your_domain.com[/email])
Password: 	your Gmail password

---

### Post by howefield on 2008-09-15
Why would he use the pop server name when setting up an IMAP account ?

---

### Post by Thelasko on 2008-09-15
> **howefield said:**
> Why would he use the pop server name when setting up an IMAP account ?

Woops!  I need to read more carefully.

Here are the [IMAP settings.]("http://mail.google.com/support/bin/answer.py?hl=en&answer=78799")

Incoming Mail (IMAP) Server - imap.gmail.com
[INDENT][INDENT][INDENT][INDENT]Use SSL: Yes[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]Port: 993[/INDENT][/INDENT][/INDENT][/INDENT]
Outgoing Mail (SMTP) Server - smtp.gmail.com (use authentication)
[INDENT][INDENT][INDENT][INDENT]Use Authentication: Yes[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]Use STARTTLS: Yes (some clients call this SSL)[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]Port: 465 or 587[/INDENT][/INDENT][/INDENT][/INDENT]
Account Name: 	your full email address (including @gmail.com) Google Apps users, please enter [email]username@your_domain.com[/email]

Email Address: 	your full Gmail email address (username@gmail.com) Google Apps users, please enter [email]username@your_domain.com[/email]

Password: 	your Gmail password

---

### Post by _sAm_ on 2008-09-15
He cant enter the port himself, Evolution will do it when he choose SSL and STARTTLS(just so he dont look for it).

---

### Post by raymondvillain on 2008-09-15
Thanks so much for all the help, folks.  But in the evolution setup assistant, where it asks for server, do I use the incoming server or the outgoing server?  I think that evolution ought to know both server names, should it not?

---

### Post by zephyrcat on 2008-09-15
I while ago I wrote a tutorial on this. I think it might help, since it covers both the Evolution steps and the GMail steps. You can find it here:

[http://www.linuxloop.com/gmailevolution/index.shtml](http://www.linuxloop.com/gmailevolution/index.shtml)

---

### Post by crazypenguin2008 on 2008-09-15
i use rocket mail. can evoloution be setup to work with rocket mail?

---

### Post by raymondvillain on 2008-09-15
Got it!  Zephyrcat's tutorial was the clincher.  Thanks to all for your time and helpfulness.

raymondvillain

---

### Post by raymondvillain on 2008-09-15
But one more thing.  Is it possible to set up Evolution to handle email from more than one ISP?  Such as Gmail and Hotmail both?

---

### Post by zephyrcat on 2008-09-15
Glad my tutorial helped!

Yes, it is possible, I believe. I am not sure of the exact steps, but it is probably something like going to File > Add Account. Just look through the menus and I bet you will find something.

---

### Post by raymondvillain on 2008-09-16
RE adding more accounts to evolution.  I did find it, under "Edit > Preferences > Add"  and off you go!  Thanks again.

---

