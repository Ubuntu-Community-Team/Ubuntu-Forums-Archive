---
title: "problem with mail"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by echohello on 2008-11-08
I am using the 'mail' program but I can't send emails to
the outside world?

---

### Post by B34ST1Y on 2008-11-08
sounds like a problem with your mailserver, not your computer. The problem *may* lie in the smtp (outgoing) server

---

### Post by echohello on 2008-11-08
Do you have any more information?

---

### Post by pgorillaman on 2008-11-08
You probably have a log file in /var/log for the mail server that probably has some detailed info.

---

### Post by pgorillaman on 2008-11-08
I believe that the mailutils deamons are either pop3d or imap3d. You might want to ps for those instead of mail.

---

### Post by echohello on 2008-11-08
Mailing to remote domains not supported -

this is the error message

---

### Post by jaya28inside on 2011-03-31
no wonder... so how to solve this warning?
> Mailing to Remote domains not supported

>> ??

---

### Post by Blasphemist on 2011-03-31
I'm assuming you're using Evolution. What did you use for your sending email server type? If your email account is Gmail or similar Evolution should have configured this right unless you changed something when you first started it. 

Anyway, what type of email account is it?

---

### Post by jaya28inside on 2011-04-01
what's that? Evolution? What's that?
I just try the sending mail steps via Ubuntu...
to my gmail as my destination but it seems failed and giving me that warning at the log report file. :confused:

---

### Post by ayenack on 2011-04-01
Evolutions is the default E-mail client in Ubuntu.

This is a good guide for setting up E-mail using a Gmail account and Evolution.

[http://greeennotebook.com/2010/06/syncing-gmail-and-evolution-contacts-calendars-and-mail-in-ubuntu-10-04/](http://greeennotebook.com/2010/06/syncing-gmail-and-evolution-contacts-calendars-and-mail-in-ubuntu-10-04/)

It uses IMAP which will also rip all your saved messages from Gmail server.

---

### Post by IHeequ5i on 2011-04-01
It sounds like the OP may be referring to the command line 'mail' program as opposed to Evolution. IIRC, mail has to be specially configured to run across domains.

---

### Post by ayenack on 2011-04-01
> **Doomspark said:**
> It sounds like the OP may be referring to the command line 'mail' program as opposed to Evolution. IIRC, mail has to be specially configured to run across domains.

Could be. The OP needs to give some more info, but makes sense.

Wonder if the OP is running server...

---

### Post by jaya28inside on 2011-04-01
> Evolutions is the default E-mail client in Ubuntu.

yah, that one is the email client...
but, but, but...

I thought ubuntu has its own mailing service
that could be used as Php to send email without configuring 
the real email, errr....? :confused:

i juz remember there is a 1 machine linux with ubuntu
my friend owned it, and he has joomla inside of it,
with php engine as of course, and he could send email using it.
seems straight forward... isn't?

~ correct me if i'm wrong.

---

### Post by Blasphemist on 2011-04-01
Quote
[HTML] juz remember there is a 1 machine linux with ubuntu
my friend owned it, and he has joomla inside of it,
with php engine as of course, and he could send email using it.
seems straight forward... isn't?[/HTML]

There are simple open source email options that do work within Joomla. This isn't something that comes with Ubuntu or any Linux. It can be added to Joomla.

---

### Post by jaya28inside on 2011-04-01
> There are simple open source email options that do work within Joomla. This isn't something that comes with Ubuntu or any Linux. It can be added to Joomla.

so, in other words...
ubuntu doesn't have its own mailing services 
as Mail Server does?

Hmmm... i thought, within ubuntu
we could do not just as email client... :P

---

### Post by Blasphemist on 2011-04-01
I found something that I think is for Ubuntu server but you can look into it.
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

This is one of the things I found for Joomla.
[http://extensions.joomla.org/extensions/contacts-and-feedback/email/4926](http://extensions.joomla.org/extensions/contacts-and-feedback/email/4926)

Here is the list of Joomla mail extensions.
[http://extensions.joomla.org/extensions/contacts-and-feedback/email](http://extensions.joomla.org/extensions/contacts-and-feedback/email)

I should have asked earlier just how you'd like to use this mail. I send, receive, etc. from evolution or using my web based email from the browser. What would you like to do? I have LAMP and Drupal on my laptop and haven't tried to set up email in Drupal.

---

### Post by jaya28inside on 2011-04-03
> I found something that I think is for Ubuntu server but you can look into it.
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

okay, Blasphemist. I will try to use that one. :D

---

