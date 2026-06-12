---
title: "Can't send EMAIL."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by grandsatrap on 2008-07-28
I am trying to install Postfix. All I need is to be able to send email out from my Ubuntu computer. My computer is behind a router and an ADSL modem. My Windows computers have no trouble sending an receiving email. They do it by going through my ISP (smtp.myisp.com).

I tried following various instructions on the internet, but none of them work (or I can't understand them).
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) but it has all sorts of SASL and TLS stuff that I don't know what it is and surely don't need.

I am now trying to follow [http://flurdy.com/docs/postfix/index...fig-simple-mta](http://flurdy.com/docs/postfix/index...fig-simple-mta)

This makes me think that postfix is running:
1. ps -ef | grep postfix
root 13052 1 0 Jul06 ? 00:00:00 /usr/lib/postfix/master
postfix 23626 13052 0 20:17 ? 00:00:00 pickup -l -t fifo -u -c
postfix 23627 13052 0 20:17 ? 00:00:00 qmgr -l -t fifo -u
satrap 23709 23535 0 20:26 pts/0 00:00:00 grep postfix

But this makes me think that it is not running:
2. telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.


Please help! At the bare minimum, I need to be able to send one email message out per day - not encrypted or anything.
Looking at the Postfix documentation, I can't tell whether the email should go though my ISP's smtp server or be sent out directly in some magical way.

I need to get this working by the end of the week.

---

### Post by halitech on 2008-07-28
> 
But this makes me think that it is not running:
2. telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.


this means it is running and you connected to it. Depending on your ISP, they may have port 25 blocked (anti spam measures to keep possibly infected computers from sending out spam). is there a reason why you don't just use your ISP outgoing mail servers?

---

### Post by Yannick Le Saint kyncani on 2008-07-28
> **grandsatrap said:**
> I am trying to install Postfix. All I need is to be able to send email out from my Ubuntu computer.
[snip]
Looking at the Postfix documentation, I can't tell whether the email should go though my ISP's smtp server or be sent out directly in some magical way.


If all you need is to send email, you can configure your mail client to use your isp's smtp server. You don't need postfix to do that. (and that would be my advice ).

If you really want to use postfix for some other reason, you can easily configure it with "sudo dpkg-reconfigure postfix". You want "internet with smarthost", use your isp's smtp server, setup your mail clients to use your local postfix smtp server. Check logs and debug your conf with "tail -f /var/log/mail.log".

---

### Post by grandsatrap on 2008-07-28
1. All the the telnet localhost 25 tells me is that I can telnet to that port. It doesn't tell me that postfix is running on that port. I can type HELO or ehlo localhost - and get nothing back.
 

I am on a dynamic IP address. If there is a power failure, my IP address changes. What I need to do is send a short text file containing my IP out using cron. I was going to use cron to use ssh's scp, but I need to type in my passphrase each time. Now I am trying to email it out. I need to know the IP address so that I can access my Ubuntu computer from the internet. Nothing fancy. Just emailing one textfile to one email address.

Thanks, please continue to help.

---

### Post by halitech on 2008-07-28
so basically you want to be able to access your computer from outside locations. Why not use something like no-ip.com or dyndns.com and create a hostname that you can update?

---

### Post by grandsatrap on 2008-07-28
> **Yannick Le Saint kyncani said:**
> If all you need is to send email, you can configure your mail client to use your isp's smtp server. You don't need postfix to do that. (and that would be my advice ). 

I don't know how to do what you are just saying. But I am happy to do it the simplest way possible.
I don't want to use Evolution/GUI mail because I don't know how to configure it to send a textfile using cron.

I don't know what you mean by "smarthost"

Thanks again.

---

### Post by halitech on 2008-07-28
the fact that it says connected tells me it is connected

if you just need to keep an updated address, why not create an account at dyndns.com or no-ip.com and set up a script or use their software to keep it updated? then you just need to remember the hostname and everything else will be in the background

---

### Post by grandsatrap on 2008-07-28
> **halitech said:**
> so basically you want to be able to access your computer from outside locations. Why not use something like no-ip.com or dyndns.com and create a hostname that you can update?

I don't really want to pay for something when it is something that Unix can do easily enough by itself. I should be able to learn how to do it.

---

### Post by halitech on 2008-07-28
> **grandsatrap said:**
> I don't really want to pay for something when it is something that Unix can do easily enough by itself. I should be able to learn how to do it.

pay? who said anything about paying? both services have free accounts (I'm using dyndns.com with 3 different hostnames) that work fine.

---

### Post by grandsatrap on 2008-07-28
Ok, let's not get distracted here.
I want to set up a shell script that is run by cron. This script will do something like "mail -s [email]externaluser@yahoo.com[/email] < myipnum.txt"
That is all that I want. 
I can get cron working.
I think can write the script.
I just can't get the mail working. This seems like a newbie thing, that's why I am posting it here.
Holy smoke! "sudo tail -f /var/log/mail.log" has a bunch of stuff in it. I don't know what it means.  

*If this works then I can send more complicated messages at predetermined times to predetermined email addresses - this could be quite useful in the long term.*

---

### Post by Yannick Le Saint kyncani on 2008-07-28
Well, (first I agree with halitech and setting up a dyndns client is very easy).

But, if you want to send email with cron, you could either set up postfix and use the MAILTO variable, or use sendemail. Using sendemail is the easiest.

Regards.

---

### Post by Fibonacci on 2008-07-30
I wanted to get postfix to work for exactly the same reasons as the OP. After trying all the suggestions here with no luck, I found that both ddclient and inadyn were in the Universe repos. The former is much easier to use - see [https://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](https://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html) .
Still, it would be nice to see how this is solved.

---

### Post by grandsatrap on 2008-07-31
> **Fibonacci said:**
> I wanted to get postfix to work for exactly the same reasons as the OP. After trying all the suggestions here with no luck, I found that both ddclient and inadyn were in the Universe repos. The former is much easier to use - see [https://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](https://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html) .
Still, it would be nice to see how this is solved.

Hey! I got it working! I am also looking into ddclient.

See my other posting on Ubuntu forums about this: [http://ubuntuforums.org/showpost.php?p=5499953&postcount=6]("http://ubuntuforums.org/showpost.php?p=5499953&postcount=6")

---

### Post by asadqamber on 2009-07-06
> **Yannick Le Saint kyncani said:**
> Well, (first I agree with halitech and setting up a dyndns client is very easy).

But, if you want to send email with cron, you could either set up postfix and use the MAILTO variable, or use sendemail. Using sendemail is the easiest.

Regards.


Hi. I am trying to use sendemail. I just don't understand the syntax. I have installed the sendemail, but I have no idea how to use it. can you help me. I tried:

sendemail -f [email]MYADRESS@gmail.com[/email] -u "the subject" -m "this is a tet mail"

---

### Post by Yannick Le Saint kyncani on 2009-07-08
Sending email with sendemail is like with any other mail client (evolution, kmail, ...).

So, you're missing :

- Your smtp server : -s smtp.my-isp.com
- The person you want the mail delivered to : -t [email]somebody@someisp.com[/email]

---

