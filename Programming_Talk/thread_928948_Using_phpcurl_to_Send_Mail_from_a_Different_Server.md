---
title: "Using php/curl to Send Mail from a Different Server"
date: 2008-09-24
forum: Programming Talk
---

### Post by steve_c on 2008-09-24
In my setup there is one dedicated e-mail/web server and separate jobs servers. I'd like to be able to send an e-mail to users once a jobs server completes a job. I'd like to do that without installing sendmail on every jobs server.

One of the best ways I can think of is to put a php script on the mail/web server that just calls the PHP mail() function. So now I'm trying to do that with a script using curl on the jobs servers. Unfortunately it's not working. Right now it's totally in quick and dirty form, but if anyone can help me make it at least work I would greatly appreciate it.

---

### Post by Bachstelze on 2008-09-24
> **steve_c said:**
> I'd like to do that without installing sendmail on every jobs server.

Why not? A server without a MTA is akin to a car without a dashboard.

---

### Post by steve_c on 2008-09-24
> **HymnToLife said:**
> Why not? A server without a MTA is akin to a car without a dashboard.

For one sendmail has a history of security issues, and while I understand most of those are due to poor configuration, having another network service still provides another potential avenue for exploit.

Also and possibly more significantly I would prefer to keep mail handling and web page serving centralized. It's easier for logging and auditing, and it's easier that if any changes have to be made that they are done to a single central server rather than on a dozen separate servers.

---

### Post by drubin on 2008-09-24
[http://phpmailer.sourceforge.net/](http://phpmailer.sourceforge.net/) 

This might help you. It is a simple class that allows you to send emails to any mail server.

---

