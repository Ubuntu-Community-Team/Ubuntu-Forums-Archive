---
title: "sendmail pointing to a pop server"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by gibovski on 2008-09-26
Hi All. 
I'm new to Ubuntu but not so new to Unix. 
I'm trying to setup ubuntu at home as a toy webserver. I want to setup sendmail or mailx or some sort of command line mail software to allow me to send mail from perl cgi. I want to use my ISP's pop server to send mails using this however all the setups I've seen for sendmail use SMTP (my ISP only offers a pop server) 
Does anyone know how to achieve what I'm after? 

Your help is appreciated...

---

### Post by Peter09 on 2008-09-26
POP service is for incoming.
SMTP is for outgoing.

---

### Post by gibovski on 2008-09-29
> **Peter09 said:**
> POP service is for incoming.
SMTP is for outgoing.

Okay.

All I know is that my mail server is mail.optusnet.com.au

How can I setup either sendmail or mailx to be able to send mail from the command line?

---

### Post by Peter09 on 2008-09-29
Here is your isp's support page for windows mail. This should contain all the details you need.

[http://www.optuszoo.com.au/help/dial/connected/windows/email](http://www.optuszoo.com.au/help/dial/connected/windows/email)

---

### Post by Bachstelze on 2008-09-29
> **gibovski said:**
> 
How can I setup either sendmail or mailx to be able to send mail from the command line?

mailx doesn't need setup, only your MTA (sendmail, Postfix, Exim...) does. Which one do you have?

---

### Post by gibovski on 2008-09-29
> **HymnToLife said:**
> mailx doesn't need setup, only your MTA (sendmail, Postfix, Exim...) does. Which one do you have?

I have sendmail installed but I don't know how to configure it to point to my ISP's mail server. I have the mail servers name which is mail.optusnet.com.au but I don't know what config files need to be modified with this info. I figured /etc/mail/sendmail.conf would be a good start but I can't see anything in there that is asking for a POP or SMTP mail server name.

---

### Post by Bachstelze on 2008-09-29
Sendmail is a bit complicated to configure, and largely overkill if all you want it send mail through a smarthost. ssmtp will do that job just as well, and is much smaller and easier to configure.

```
sudo apt-get remove --purge sendmail
sudo apt-get install ssmtp
```

---

### Post by gibovski on 2008-09-29
> **HymnToLife said:**
> 
```
sudo apt-get remove --purge sendmail
sudo apt-get install ssmtp
```

Right. I successfully uninstalled sendmail as you suggested but I get an error trying to install ssmtp. The guts of the error is. 


```
Removing exim4-daemon-light ...
 * Stopping MTA                                                                 /sbin/start-stop-daemon: warning: failed to kill 5492: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-daemon-light (--remove):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 exim4-base
 exim4-daemon-light
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Some sort of software dependency issue mixed with a stop daemon failure? How can I get past this one?

---

### Post by gibovski on 2008-09-29
Got past that... I couldn't figure out how to start the exim4 daemon so I lazily rebooted the machine...

I got ssmtp installed now.. 

Still having trouble setting it all up though...

I first got a Forged Received header error.

I then modified the ssmtp.conf to put in login info for the server by adding the lines.

```
AuthUser=######
AuthPass=######
UseTLS=YES
UseSTARTTLS=YES
```


Now when I try to send mail using mailx I get. 

```
send-mail:  (optusnet.com.au)
Can't send mail: sendmail process failed with error code 1
```

And I can't find any errors in the mail logs. The only thing in /var/log/mail.err is 
```
Sep 29 19:31:34 gibuntu sSMTP[7398]:  (optusnet.com.au)
```

Any help? Advice??

Thanks for all your help so far.

---

### Post by Bachstelze on 2008-09-29
Are you sure you need TLS? Unless you are explicitly told to use it, you shouldn't. Try removing those two lines from your config.

---

### Post by gibovski on 2008-09-29
I removed those 2 lines now I'm getting a different error.

```
send-mail: 550 5.7.1 Forged Received header
Can't send mail: sendmail process failed with error code 1
```

I've searched the forum and google for the Forged header error but I got nothin...

I thought setting up command line email would be easy... Shows what I know..

---

### Post by Bachstelze on 2008-09-29
How are you trying to send mail? How about just :

```
echo "This is a test message." | mail -s Test you@domain.com
```

---

### Post by gibovski on 2008-09-30
> **HymnToLife said:**
> How are you trying to send mail? How about just :

```
echo "This is a test message." | mail -s Test you@domain.com
```


Yeah something like that except I was using mailx. I tried it with Mail and got the same error though...

```
mgibson@gibuntu:~$ echo "This is a test message." | mail -s Test you@domain.com
send-mail: 550 5.7.1 Forged Received header
Can't send mail: sendmail process failed with error code 1

```

---

