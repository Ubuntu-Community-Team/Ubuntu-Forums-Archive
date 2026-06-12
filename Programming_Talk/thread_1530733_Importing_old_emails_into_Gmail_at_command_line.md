---
title: "Importing old emails into Gmail at command line"
date: 2010-07-14
forum: Programming Talk
---

### Post by tarahmarie on 2010-07-14
Hi, all!

I'm trying to use ([http://marklyon.org/gmail/old/default.htm](http://marklyon.org/gmail/old/default.htm)) the Gmail Loader to import a couple of gigs of old emails into Gmail so they're searchable.

I've run a python hello world in my shell; it's working fine.  I try running 

~ : Yes, Supreme Empress? $ python gml.py mbox /home/tarahmarie/.kde/share/apps/kmail/mail/Old [email]myemail@gmail.com[/email] 

And I get "ERROR SENDING MESSAGE FROM" errors.  When I add an optional smtp server, as in

~ : Yes, Supreme Empress? $ python gml.py mbox /home/tarahmarie/.kde/share/apps/kmail/mail/Old [email]myemail@gmail.com[/email] gmail-smtp-in.l.google.com

I see that it's forwarding messages, but the messages never show up in my gmail.  Is there some kind of authentication problem here?

---

### Post by iponeverything on 2010-07-14
Are they going to the spam folder?

You might grab wireshark to watch the SMTP transaction, it might be tls thing.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

---

### Post by tarahmarie on 2010-07-14
Ah--yes, they are.  

Thank you very much!

---

