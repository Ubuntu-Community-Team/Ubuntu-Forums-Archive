---
title: "Mail imap issues"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by hvc123 on 2008-08-03
Hi all,

i have created a mail server but i cannot connect to it via outlook (on another machine) or squirrel webmail. the smtp imap and pop3 ports are open.

it does however receive mail to the correct /var/mail/folders. i just cant connect a client. i have routed through the mail logs but i cant find anything wrong 
i can telnet to 993,143 and 25 no problems and get the correct responses


also i see his in mail.log 
NOQUEUE: reject_warning: RCPT from (ipaddress): 504 5.5.2 <machinename>: Helo command rejected: need fully-qualified hostname; from=<email@address> to=<email@address> proto=ESMTP helo=<machinename>

.... help please

---

### Post by jamesrfla on 2008-08-03
I get a similar message with apache when I set it up. If you still are a beginner I would suggest getting webmin. ```
sudo apt-get install webmin
``` In their you can stop your mail server and squirl mail and then bring them back up and they should work. Or you can change some settings in for your mail server in webmin and see if you can find something about fully-qualified hostname. Good luck.

---

