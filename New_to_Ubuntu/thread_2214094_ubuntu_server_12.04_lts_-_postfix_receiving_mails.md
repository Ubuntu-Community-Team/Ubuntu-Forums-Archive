---
title: "ubuntu server 12.04 lts - postfix receiving mails?"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by bar2 on 2014-03-30
hello everybody,
i am purely new at the cloud servers.. almost happy.

ok, first of all - i did:
sudo apt-get update,
installed all the apache2, php5, mysql, etc. 

after all i did installed postfix, and followed many guides and instructions,
none of them explains the configurations well.
i succeed sending mails from the php by 'mail()' function, that's nice..

but the **BIG **question is how to configure incoming mails?!

i added into '[COLOR=#000000][FONT=monospace]/etc/postfix/virtual'
[/FONT][/COLOR]the line [COLOR=#000000][FONT=monospace]- '[EMAIL="admin@mydomain.com"]admin@mydomain.com[/EMAIL] admin' (of course i changed 'mydomain'..)
[/FONT][/COLOR]and finally i added the folder path to the incoming emails.

when i tried to send mail to my address, there where no failure, but either success, none file were found at the folder inbox destination.

my questions:
1. how to fix the incoming mail issue (what ports should be open if needed?)
2. is there any option to connect the mail by external mail client with pop3/imap?

that's it i think. it is super important for me because this is the only thing left undone in order to leave my old hosting completly.

* the domain DNS is working on the server's IP address, either the mail.mydomain.com.

Thanks for the helpers, 

bar.

---

### Post by apohal9 on 2014-03-30
What I've found some weeks ago:

> mail-stack-delivery - mail server delivery agent stack provided by Ubuntu server team

This is an awesome package that will install and configure and postfix with dovecot for having a complete mail server setup with smtp/pop3s/imaps working for local users.

---

