---
title: "[SOLVED] CLI - sending mail"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-18
hi, I'm learning how to send mail.  And so I apt-got "sendmail" (i am guessing here) and the terminal issued the below warning which as I understand it CRONUS is not an email address (guessing), and I ahve to change it.  Am I correct? How do I do this?

WARNING: local host name (CRONUS) is not qualified; see cf/README: WHO AM I?
/etc/mail/aliases: 1 aliases, longest 12 bytes, 16 bytes total
 
Warning: 3 database(s) sources
	were not found, (but were created)
	please investigate.
 * Starting Mail Transport Agent (MTA) sendmail                                 hostname: Unknown host
hostname: Unknown host
                                                                         [ OK ]

Setting up sensible-mda (8.14.2-2build1) ...
Setting up sendmail (8.14.2-2build1) ...

---

### Post by schwascore on 2008-07-18
sounds like you're trying to set up your computer as an e-mail server.  Here are some resources that might help:

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by adamogardner on 2008-07-18
so much for that idea.  looks complicated.  SO what would be the point of having a mail server besides screwing around with a pc which is all I want to do for now.?

---

### Post by Titan8990 on 2008-07-18
Sendmail is a **FAR** more complicated email server the postfix that he posted. 

> SO what would be the point of having a mail server besides screwing around with a pc which is all I want to do for now.?

Don't know you came here asking for help on a Email server....

---

### Post by Bachstelze on 2008-07-18
> **adamogardner said:**
> hi, I'm learning how to send mail.  And so I apt-got "sendmail"

If sending e-mail is all you want to do, go with exim. It is the default MTA in Debian and all of its derivatives, and will let you do that very easily since all you will need to configure wil be doable through debconf.

```
sudo apt-get instal exim4
```

---

### Post by adamogardner on 2008-07-18
i downloaded exim4  now I'mback at the terminal prompt.  Forgive my stupidity but what do I do now?  tee hee, go ahead and laugh, but in another 6 months I will be helping out around here.

Setting up exim4 (4.69-2) ...
oh  Agents,
not directly from a shell command line. Options and/or arguments control
what it does when called. For a list of options, see the Exim documentation

"mail user agent"?   K I'm on google...oh and "debconf?"..  this is all new to me.

---

### Post by Bachstelze on 2008-07-18
Debconf is the infrastructure Debian and all of its derivatives use to easily configure software :

```
sudo dpkg-reconfigure exim4-config
```

It will ask you a few questions. What you should answer depends greatly on your network setup and what you want to do. I assume this is a home system, right? Does it have a dynapic os static IP address (I mean the one attributed by your ISP, not the local one) ? Do you want to also be able to recieve mail on the system ?

---

### Post by adamogardner on 2008-07-18
I want the system to be as versatile as possible.

What I have is a laptop, with built in wireless thing, madwifi something.  I am trying to learn about my ip adress but it seems to change. i don't have a service provider either I just pick up random signals.  will edit shortly with what I acheive in your instruction.

which configuration suits me?

 General type of mail configuration:                                   &#9474; 
   &#9474;                                                                       &#9474; 
   &#9474;     internet site; mail is sent and received directly using SMTP      &#9474; 
   &#9474;     mail sent by smarthost; received via SMTP or fetchmail            &#9474; 
   &#9474;     mail sent by smarthost; no local mail                             &#9474; 
   &#9474;     local delivery only; not on a network                             &#9474; 
   &#9474;     no configuration at this time

---

### Post by Bachstelze on 2008-07-18
> **adamogardner said:**
> I want the system to be as versatile as possible.

What I have is a laptop, with built in wireless thing, madwifi something.  I am trying to learn about my ip adress but it seems to change. i don't have a service provider either I just pick up random signals.

Then it won't work. In order to send mail, you **must** either be able to send it yourself, which means having a static IP address, or have access to a mail relay server (usually, your ISP's).

---

### Post by adamogardner on 2008-07-18
oh.  then I'm bored.  what if my friend or family have a isp   can I send it through them?

---

### Post by Bachstelze on 2008-07-18
> **adamogardner said:**
> oh.  then I'm bored.  what if my friend or family have a isp   can I send it through them?

Certainly. The important thing is that your laptop must be connected to a network that has access to a mail relaying server.

---

### Post by adamogardner on 2008-07-18
thanks for your time today.  I like your name btw,

---

### Post by linkinanri on 2008-10-07
hi folks,

I tried to follow the instructions for "exim4-config" and finished configuration. Unfortunately I'm still not able to get my PHP mail() function working.

I have ubuntu 8.0.4 on ppc and static IP.
would any of you point me to link, and provide configuration manual how to get it working? Basically, all I need is to send out emails via email($to. $title, $msg) (I don't care about receiving)

thanks in advance

---

