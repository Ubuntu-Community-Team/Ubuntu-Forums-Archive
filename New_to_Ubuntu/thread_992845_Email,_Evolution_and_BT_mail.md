---
title: "Email, Evolution and BT mail"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by GeordieJedi on 2008-11-25
Hi again all,

I have a question re email.

I fixed my friends laptop a few weeks ago (by installing Ubuntu on it).

Now he has a BT mail account that he'd like to use with an email client program
(either evolution or thunderbird).

Now try as I might, I cant get either program to connect to his yahoo/bt mail account
to send/receive mails (or pretty much anything use full).


Ive looked at the help pages on BT own site, and they gave me the following
Settings =

Incoming mail (POP3) server : mail.btinternet.com (port 110)
Outgoing mail (SMTP) server : mail.btinternet.com (port 25)


Are there any full step-by-step guides or instructions on getting either of these
apps to work? Ive had a quick trawl through google, and got a couple of forum responses
from others trying to do the same thing, Ive tried what was suggested but still got no joy.


Evolution

Here's what I've enterd so far =

On the receiving mail tab

server = mail.btinternet.com
Where do I enter the port settings?

username = [email]persons.name@btinternet.com[/email]

Do I need to use authentication? (as it seems to get further into the process
if I don't use any before spitting its dummy out)

(I'd imagine that I should have to for security reasons - and I'd rather use it if I could)

Sending mail tab

server = mail.btinternet.com
(again, where do I put the port numbers?)

server requires authentication (I've ticked the box)

Security

Use secure connection (chosen - SSL)

Authentication

Type = Login
chosen - check for supported types)

Username = [email]persons.name@btinternet.com[/email]
remember password (ticked this box too)

NB - When Ive clicked on "check for supported types" it comes back with a
dialogue box stating the following message =

issuer: OU=Equifax Secure Certificate Authority,O=Equifax,C=US
Subject: CN=smtp.mail.yahoo.com,OU=Yahoo,O=Yahoo! Inc.,L=Santa Clara,ST=California,C=US
Fingerprint: 5e:37:38:d6:a5:d5:00:99:b7:e3:7b:6a:ac:04:7f:92
Signature: BAD

So I always click on No when prompted at this point.

If I choose no encryption, when it asks for the password (& I'm certain that
I enter it correctly). It tells me that its refused the connection.

NB - I can get get access to the email account if I log in via a web browser

Sorry about the loooong post, cheers for taking the time to read it.
Any help would be gratefully appreciated. Thanks in advance.

---

### Post by madsc89 on 2008-11-25
I don't know what BT is:p, but I've got a suggestion for yahoo.

I recommend you try thunderbird with webmail plugins. I've got good experience with both.

Install ThunderBird, Open it and choose Tools -> Add-ons. This will open up a window with your installed add.ons.
Go to this site: [http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)
Download WebMail, _and_ the yahoo one. (right click, save link as, choose your desktop) Then simply drag the two files into the previously opened window. Take the clean webmail one first (just in case).
Then restart TB, and create a new account. choose Yahoo.

Have only tried Hotmail, myself, but I would think yahoo is easier.

---

### Post by fatphilthethird on 2008-11-25
Hi

Shouldn't the outgoing address be smtp.btinternet.com, rather than mail.btinternet.com?

---

### Post by FreewheelinFrank on 2008-11-25
Here's a working setup for receiving email.

(My email address is @btopenworld.com, so I use mail.btopenworld.com)

I must've bookmarked the link I used somewhere- I'll have a look for it.

---

### Post by fatphilthethird on 2008-11-25
Think you may be right:

[http://www.btopenworld.com/faqs/manual_email_setup](http://www.btopenworld.com/faqs/manual_email_setup)

---

### Post by FreewheelinFrank on 2008-11-25
And for sending:

---

### Post by fatphilthethird on 2008-11-25
> issuer: OU=Equifax Secure Certificate Authority,O=Equifax,C=US
Subject: CN=smtp.mail.yahoo.com,OU=Yahoo,O=Yahoo! Inc.,L=Santa Clara,ST=California,C=US
Fingerprint: 5e:37:38:d6:a5:d5:00:99:b7:e3:7b:6a:ac:04:7f:92
Signature: BAD

So I always click on No when prompted at this point.

What happends if you click yes?

---

### Post by ged5 on 2008-12-01
Did you manage to sort this out. I'm trying to connect to bt with Evolution and have the same problem.

Thanks

Ged

---

### Post by Kellemora on 2008-12-01
Hi GJ

Instead of messing with those wanna-be awkward programs, why not install WINE and then Install Eudora 7.1!

I've used Eudora since like day one and have never found anything better.  So needless to say, I was totally Elated when I found out it runs under Wine perfectly!

We get over 1,600 e-mails per day, mostly spam that gets junked out, but it hasn't balked yet at the load!

TTUL
Gary

---

### Post by GeordieJedi on 2008-12-04
Cheers for all the help and advice people,
madsc89, fatphilthethird, FreewheelinFrank, ged5 and Kellemora

However I did manage to get it to work (albeit a bit of a workaround/cheat?)

I just set him up with a Googlemail account. (made sure that evolution would work
 with it firstly, then forwarded all the mails from BT to Google and,
 bish bash bosh....working emails in evolution.

Whey!


@ ged5
"HINTERG" from another forum (Linux format).  Suggested that it may be,
 due to me putting the whole email address in the username field, rather than just the
 first part of the address before the @ symbol

EG:
persons.name

rather than
[email]persons.name@btinternet.com[/email]

---

### Post by ged5 on 2008-12-04
> **GeordieJedi said:**
> 

@ ged5
"HINTERG" from another forum (Linux format).  Suggested that it may be,
 due to me putting the whole email address in the username field, rather than just the
 first part of the address before the @ symbol

EG:
persons.name

rather than
[email]persons.name@btinternet.com[/email]

Thanks, that could well be it as I think it had put just the name in and I added the   @btinternet.com   because that was how it worked in Outlook Express.  

I have already installed and got Thunderbird working :D
So bye bye windoze ):P

Ged

---

### Post by Mike Withers on 2009-01-01
I am trying to set up Evolution 2.24.1 having downloaded the Ubuntu software onto a CD to run on a different PC. At this stage still running Ubuntu off the CD before a formal instal.

After setting up Evolution as described, I still keep on getting "Name or service not known" as an error message..

HELP!

---

### Post by Mike Withers on 2009-01-01
I am trying to set up Evolution 2.24.1 having downloaded the Ubuntu software onto a CD to run on a different PC. At this stage still running Ubuntu off the CD before a formal instal.

After setting up Evolution as described, I still keep on getting "Name or service not known" as an error message..

HELP!

---

### Post by Alan Gammon on 2009-01-03
I am very new to Linux, (loke four days) but have encountered the same problem as the contributor below.  I have downloaded a copy of Crossover, to allow me to run MS Office (2003).  So far, so good!  However, in MS Outlook, I cannot send or receive e-mails.  I have configured outlook as when used in MS Vista, i.e.all setting.  However, NOTHING!  It tells me it has "timed out waiting for a response from the server", yet I know the server is there and I can send and receive e-mails on my other lap top (running windows) as normal.  What is even more puzzling, is I can send, but not receive in Pigion?
Help please.
  

> **GeordieJedi said:**
> Hi again all,

I have a question re email.

I fixed my friends laptop a few weeks ago (by installing Ubuntu on it).

Now he has a BT mail account that he'd like to use with an email client program
(either evolution or thunderbird).

Now try as I might, I cant get either program to connect to his yahoo/bt mail account
to send/receive mails (or pretty much anything use full).


Ive looked at the help pages on BT own site, and they gave me the following
Settings =

Incoming mail (POP3) server : mail.btinternet.com (port 110)
Outgoing mail (SMTP) server : mail.btinternet.com (port 25)


Are there any full step-by-step guides or instructions on getting either of these
apps to work? Ive had a quick trawl through google, and got a couple of forum responses
from others trying to do the same thing, Ive tried what was suggested but still got no joy.


Evolution

Here's what I've enterd so far =

On the receiving mail tab

server = mail.btinternet.com
Where do I enter the port settings?

username = [EMAIL="persons.name@btinternet.com"]persons.name@btinternet.com[/EMAIL]

Do I need to use authentication? (as it seems to get further into the process
if I don't use any before spitting its dummy out)

(I'd imagine that I should have to for security reasons - and I'd rather use it if I could)

Sending mail tab

server = mail.btinternet.com
(again, where do I put the port numbers?)

server requires authentication (I've ticked the box)

Security

Use secure connection (chosen - SSL)

Authentication

Type = Login
chosen - check for supported types)

Username = [EMAIL="persons.name@btinternet.com"]persons.name@btinternet.com[/EMAIL]
remember password (ticked this box too)

NB - When Ive clicked on "check for supported types" it comes back with a
dialogue box stating the following message =

issuer: OU=Equifax Secure Certificate Authority,O=Equifax,C=US
Subject: CN=smtp.mail.yahoo.com,OU=Yahoo,O=Yahoo! Inc.,L=Santa Clara,ST=California,C=US
Fingerprint: 5e:37:38:d6:a5:d5:00:99:b7:e3:7b:6a:ac:04:7f:92
Signature: BAD

So I always click on No when prompted at this point.

If I choose no encryption, when it asks for the password (& I'm certain that
I enter it correctly). It tells me that its refused the connection.

NB - I can get get access to the email account if I log in via a web browser

Sorry about the loooong post, cheers for taking the time to read it.
Any help would be gratefully appreciated. Thanks in advance.

---

### Post by rwtevo on 2009-11-04
Hi. If anyone wants to get evolution set up with BT internet, here's how I did it :

Enter you name and email address as requested.

**Receiving email** :

Server type = POP

Server = mail.btinternet.com

Username = the bit of your email before @btinternet.com

**Sending email** : server type = SMTP

Server : smtp.btinternet.com

MAKE SURE SERVER REQUIRES AUTHENTICATION IS TICKED

Security  = no encryption

Authentication = plain

Username = the bit of your email before @btinternet.com

And that's it.

Certainly works fine for me.

Cheers.

---

