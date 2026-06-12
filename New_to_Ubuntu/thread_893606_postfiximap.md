---
title: "postfix/imap"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by ub007 on 2008-08-18
Hi,

I'm installing a mail server on Ubuntu with MTA postfix and MDA:courier IMAP.Sending and receiving mails on the localhost works fine.How do i extend it to my local intranet.....

This is how my /etc/postfix/main.cf looks like

> myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mynetworks = 127.0.0.0/8, 192.168.11.2/24
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all


And these are my entries for /etc/postfix/vmaps

> info@ub.surey.ac.uk  ub.surey.ac.uk/info/
[email]david@ub.surey.ac.uk[/email] ub.surey.ac.uk/david/

/etc/postfix/vhosts reads

> ub.surey.ac.uk

I'm able to send mails to [email]info@ub.surey.ac.uk[/email] and [email]david@ub.surey.ac.uk[/email] as root.

I can find them at /home/vmail/ub.surey.ac.uk/info/new & /home/vmail/ub.surey.ac.uk/david/new

Now how can i test this mail set up from a remote machine on the intranet?
What i need to do is send & recieve mails to [email]david@ub.surey.ac.uk[/email] from the other PCs on my local intranet.In effect that would provide an email system for my intranet.I'm not using DNS,however i have all the system names are included in /etc/hosts.Thanks in advance

Cheers
David

---

