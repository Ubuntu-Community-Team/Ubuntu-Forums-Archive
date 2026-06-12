---
title: "Evolution Mail"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by bolter40k on 2008-07-26
I'm sure you are all sick of people asking this question but... I have done extensive searching on setting up evolution mail with an att email account however i still cannot get evolution mail to work properly.  I get this message:  Host lookup failed: imailhost.worldnet.att: Name or service not known.  

My current settings in evolution mail

Recieving Mail
   server type POP
   server pop.att.yahoo.com
   ssl encryption
   authentication login

Sending Mail
   server type SMTP
   server smtp.att.yahoo.com
   ssl encryption
   authentication login

---

### Post by lisati on 2008-07-26
I'm not an at&t customer, but I'm guessing that the settings for Outlook shown at [http://office.microsoft.com/en-us/outlook/HA011134351033.aspx](http://office.microsoft.com/en-us/outlook/HA011134351033.aspx) might be of some help - click on the link for "Add your AT&T Worldnet e-mail account"

---

### Post by bolter40k on 2008-07-26
when i first tried setting this up i gave it that host but i am not a world net user and thats the problem i think and i dont know how to change it

---

### Post by quinnten83 on 2008-07-26
might be a port issue.
try setting the mail address up with the port number directly behind it e.g.
[email]you@yourprovider.com[/email]:59
Check which port is required and which type of encryption.

---

### Post by bolter40k on 2008-07-26
> **quinnten83 said:**
> might be a port issue.
try setting the mail address up with the port number directly behind it e.g.
[email]you@yourprovider.com[/email]:59
Check which port is required and which type of encryption.
i have the ports open, it still gives me the same error mesage.  If i were to uninstall it and reinstall it would it give me the chance to reset the host, however when i try to uninstall it i get a mesage about programs depending on it and i have to use something else to do it

---

### Post by lisati on 2008-07-26
Most of the email providers I've used have a "help" page which will give you the names of the servers etc to enter. For a Yahoo account it's usually something like pop.**mail**.yahoo.com and smtp.**mail**.yahoo.com, and the option to enable  POP access must be set (the OP is the first time I've seen "pop.**att**.yahoo.com" and "smtp.**att**.yahoo.com", which could be the reason Evolution is looking for the worldnet server)

---

