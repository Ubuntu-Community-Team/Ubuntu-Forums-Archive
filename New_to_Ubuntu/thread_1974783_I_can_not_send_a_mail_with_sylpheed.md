---
title: "I can not send a mail with sylpheed"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by knuti1960 on 2012-05-06
I want to use my hotmail-account in sylpheed: It is like myname [at] live.de
hotmail told me to use the following servers:
 
>  
POP3-Server: pop3.live.com (Port 995)
SMTP Server: smtp.live.com (Port 25)
 
They also told me to use:

> SSL for POP3 and SMTP
SMTP- Authentification

I did all that in sylpheed,but:

 
I can get mails but I can not send messages,after about 50 seconds I get the message,that the time for the session is over and the message is not send.
I am using Sylpheed 3.2.0beta3, Lubuntu 11.10
My laptop is an old IBM A22m, only 256 MB RAM,850 MHz, 10GB HD. Thats why I chose Lubuntu. Until now it works fine, but sylpheed does not.
I´m new to Linux, not very much experiance with computers,until now I worked with windows as OS.
 
Best greatings from Germany,
Knud

---

### Post by Rex Bouwense on 2012-05-06
Unless I read it wrong, you have done everything correctly.  If you have another email account I would try to set it up with Sylpheed.  I do not use Sylpheed but I have it installed so I just set it up with one of my email accounts.  It is pretty standard.  I would delete the account and set it up again.  I did notice in account preferences-> SSL it says if you have a problem turn it off.  Try that first before you delete and set up the account again.
By the way welcome to the forums.

---

### Post by knuti1960 on 2012-05-06
O.k., I tried it without SSL, I tried it several times with a new account.
But it does not work.
Is it possible,that it has to do with the router? I´m not sure,but I think the router has a kind of firewall.It is a Fritz-Box 3270.
 
Thank you for the welcome.

---

### Post by Rodney9 on 2012-05-06
This may help, mentions using another port - [http://www.ghacks.net/2009/03/14/hotmail-pop3-configuration/](http://www.ghacks.net/2009/03/14/hotmail-pop3-configuration/)

Another email alternative is Claws Mail, is still lightweight but has many more features - [http://www.claws-mail.org/](http://www.claws-mail.org/)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Rex Bouwense on 2012-05-06
Make sure that your firewall allows Sylpheed access to the Internet.  I have been using Thunderbird for so long I guess I have been spoiled.  I just download and install and it works and always has in the past.

---

### Post by Rex Bouwense on 2012-05-06
That is the web site I was looking for.  Good job Rodney9.  I knew there was an alternate port but for the life of me I could not remember what it was.  Got it now.  Hope it works for the OP.

---

### Post by knuti1960 on 2012-05-08
It is not the firewall.I have checked the router.

It seems,as if my computer does not connect to the server smtp.live.com
I always get the message: Error,time exceeded **after about 50 seconds**.That has to be time enough for a little mail :-)

Changing to claws: The same error-warning.

I have three of these older notebooks,on each is lubuntu installed, on each I have these problems.

---

### Post by runningcake on 2013-01-11
Hi, this worked for me in being able to send email from Hotmail. Go-to "Configuration" menu and select "Preferences for current account...". Next select the "SSL" tab, look under "Send (SMTP)" heading and change "Use SSl for SMTP connection" to "Use STARTTLS command to start SSL session". Hope this helps.

---

### Post by knuti1960 on 2013-01-11
> **runningcake said:**
>  "Use STARTTLS command to start SSL session".
This was the solution. I found it in 5/12 somewhere in the internet, but forgot to post here, sorry.
Nevertheless, thank you !!

---

