---
title: "Evolution doesn't fetch my gmail inbox"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by macscrai on 2008-07-20
Hello everyone,

I am having problems with Evolution mail and fetching my gmail inbox.

I have set up Evolution to all the settings gmail has listed on their site, and also enabled pop and IMAP in gmail settings. With everything set up I still cannot reach my inbox. SMTP works for sending mail and I have used Evolution before with 7.10 (and it worked) but I have no idea why It isn't working now.

I am using:

pop.gmail.com (tried with and without port 995)
My full email address as my username.
SSL encryption
Password authentication

BTW I have also tried IMAP but with no avail.

---

### Post by neurostu on 2008-07-20
I currently use evolution to fetch email from gmail too, although every couple of days it goes buggy... for some reason gmail (in my experience) has problems with imap and pop.

---

### Post by ejpyle on 2008-07-20
> **macscrai said:**
> Hello everyone,

I am having problems with Evolution mail and fetching my gmail inbox.

I have set up Evolution to all the settings gmail has listed on their site, and also enabled pop and IMAP in gmail settings. With everything set up I still cannot reach my inbox. SMTP works for sending mail and I have used Evolution before with 7.10 (and it worked) but I have no idea why It isn't working now.

I am using:

pop.gmail.com (tried with and without port 995)
My full email address as my username.
SSL encryption
Password authentication

BTW I have also tried IMAP but with no avail.

set it up the way they outline it here....
[http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)

if it does not work do not worry....I am having the same problem and it is not on your end...it is on google's end.

---

### Post by mdsharp24 on 2008-07-20
Don't use your FULL email address, just the part BEFORE @gmail.com

pop= SSL
smtp= TLS

---

### Post by macscrai on 2008-07-20
I have already set it up using Google's page there and have also tries what mdsharp24 suggested with No luck. Can anyone else get their email? If it was a Google thing would it be widespread?

Thanks

---

### Post by t0p on 2008-07-20
I get my email from my gmail account using POP.  I followed the prompts in Evolution to set up my account details - I gave my full email address (name@gmail.com), elected to receive over POP, encrypted with SSL.  I can send and receive with no problems.

---

### Post by YoutubesUbunuLee on 2008-07-20
> **macscrai said:**
> Hello everyone,

I am having problems with Evolution mail and fetching my gmail inbox.

I have set up Evolution to all the settings gmail has listed on their site, and also enabled pop and IMAP in gmail settings. With everything set up I still cannot reach my inbox. SMTP works for sending mail and I have used Evolution before with 7.10 (and it worked) but I have no idea why It isn't working now.

I am using:

pop.gmail.com (tried with and without port 995)
My full email address as my username.
SSL encryption
Password authentication

BTW I have also tried IMAP but with no avail.


sudo apt-get checkgmail

It will show up in your system tray and give you updates. 
To add it to startup go to System / Preferences / Sessions.
Make the name Gmail Checker and the command checkgmail
;)

---

### Post by YoutubesUbunuLee on 2008-07-20
> **YoutubesUbunuLee said:**
> sudo apt-get checkgmail

It will show up in your system tray and give you updates. 
To add it to startup go to System / Preferences / Sessions.
Make the name Gmail Checker and the command checkgmail
;)

I mean,

sudo apt-get install checkgmail

-_- my bad

---

### Post by suprfish on 2008-07-20
Configuration to access my gmail account w/ Evolution. Note: authentication under 'sending email' can be either PLAIN or "Login", not sure what the exact difference is but it shouldn't matter much since it's SSL.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78419&stc=1&d=1216610938[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78420&stc=1&d=1216610938[/IMG]

IMO gmail POP updates are a bit delayed. Hope this helps.

---

### Post by duckfeet on 2008-07-20
I finally checked out Thunderbird, and found it much better, simpler, and easier to setup for mail...I'm glad I tried it...plus app is put out by Mozilla, same as browser...

---

### Post by macscrai on 2008-07-21
I don't know if it is Evolution or Gmail's fault but apparently it doesn't download mail that you send yourself.

I am receiving all other email except stuff I email to myself, which would be handy if I could since I archive code in my inbox sometimes.

Does it do this for everyone, or is it a setting I can change?


-Thanks

---

### Post by suprfish on 2008-07-21
> **duckfeet said:**
> I finally checked out Thunderbird, and found it much better, simpler, and easier to setup for mail...I'm glad I tried it...plus app is put out by Mozilla, same as browser...

I use Evolution because it is somewhat integrated into the gnome desktop, e.g. the calendar/planner.

> **macscrai said:**
> I don't know if it is Evolution or Gmail's fault but apparently it doesn't download mail that you send yourself.

I am receiving all other email except stuff I email to myself, which would be handy if I could since I archive code in my inbox sometimes.

Does it do this for everyone, or is it a setting I can change?


-Thanks

I think it might just be email that you send to yourself from Evolution (should be available in the 'Sent' folder). When I send an email to myself from the gmail website, Evolution downloads it.

---

### Post by t0p on 2008-07-21
> **macscrai said:**
> I don't know if it is Evolution or Gmail's fault but apparently it doesn't download mail that you send yourself.

I am receiving all other email except stuff I email to myself, which would be handy if I could since I archive code in my inbox sometimes.

Does it do this for everyone, or is it a setting I can change?


Doesn't it appear in the **Sent** box?

**EDIT:** *Whoops*, suprfish already suggested this!

---

### Post by macscrai on 2008-07-21
I have gotten everything sorted out, Evolution still doesn't download the messages that I send myself from Evolution. Though it seems more logical just to look in my sent items folder.

BTW I have chosen Evolution because of the Gnome desktop integration with calender etc.

Thanks for all the help,

-Craig

---

