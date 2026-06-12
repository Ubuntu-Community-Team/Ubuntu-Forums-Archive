---
title: "Mail Settings Problem"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by hawk007 on 2012-09-15
Ok so i have 2 servers.

1 x Ubuntu                   IP 192.168.1.7
1 x windows Server 2003      IP 192.168.1.6

I have a script on the ubuntu server which works apart from the mail function. When i try to send an email to a user (to test) it doesnt send.

The windows server 192.168.1.6 hosts the mailserver. Mail Enable.


**PHP settings on the ubuntu:**

SMTP = 192.168.1.6
SMTP_Port = 25
Send Mail from [email]me@mydomain.com[/email]


**Script Config Settings For SMTP:**

Mailer_send_method = "php"
smtp_host "192.168.1.6" (the windows machine)
smtp_authentication "false"
smtp_user "smtp_user"
smtp_password "smtp_password"
(script states username and password only needed when TYPE is "sendmail". Its "php".
smap_port "25"


**Windows Server SMTP Settings**

PHP settings:

smtp 127.0.0.1
smtp_port 25
Sendmail_from [email]me@domainname2.com[/email] (different from ubuntu php?)

I have the domain name hosted on the windows server, MX and A records for the domain.com are in the dns server. (SimpleDNS)

I am using LOCAL STATIC IP ing here, but i have 2 STATIC IPs supplied by my ISP.

All of my zonefiles are using LOCAL STATIC IPs as are my TCP/IP settings on both servers.

To access my websites outside my network i simply change the IP in my simpleDNS Zone Files to the relevent EXTERNAL STATIC IP.

Does anyone have a clue as to what could be wrong here. Why the script wont mail out. Is it because im using local/LAN side static IPs? 

Im no expert but i think everything i set up ok. I can send mail from the windows mailserver/mailenable account me?mydomain.com to my gmail account and the message gets sent ok.

Any advice appreciated thanks.

---

### Post by daslinkard on 2012-09-21
Have you tried using smtp port 2525 as the default port of 25 may be blocked by your ISP?

---

