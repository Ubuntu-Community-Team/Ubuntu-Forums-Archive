---
title: "how to setup an evolution email account"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by algen on 2013-04-21
from a very new ubundu (or linux) user.

---

### Post by Sef on 2013-04-21
Moved to Absolute Beginnners.

---

### Post by claracc on 2013-04-21
Follow the following step by step tutorial: [http://www.howtoforge.com/how-to-configure-an-email-account-in-evolution](http://www.howtoforge.com/how-to-configure-an-email-account-in-evolution)

---

### Post by algen on 2013-04-22
The step by step tutorial at:  [http://www.howtoforge.com/how-to-con...t-in-evolution]("http://www.howtoforge.com/how-to-configure-an-email-account-in-evolution")  
didn't work.  Now I can't get into the 'Evolution Setup Assistant' to try another method.
Does anyone have an ideal on accessing the 'assistant' again.  I would appreciate any
help that may be offered.  [email]algen37@yahoo.com[/email] -

---

### Post by black veils on 2013-04-22
firstly that info was for pop only, you may need imap. 

what is your email provider? gmail, yahoo, hotmail etc 

and what are you expecting?

---

### Post by singlebinary on 2013-04-26
I have the same difficulty. I never used Evolution before but after upgrading to 13.04, I decided to install Evolution.  However, I am unable to receive and send emails. The configuration I use is pretty standard and still I have no access to emails. Please help! 


Below are the settings I have used: 

NOTE: I have IMAP enabled on Gmail. 

Receiving Email: 
----------------------

Server Type: IMAP+ 

Configuration: 
Server: imap.gmail.com; Port: 993
Username: *******@gmail.com

Security
Encryption method: SSL on a dedicated port 

Authentication
Password  Check for Supported Types
---------------------------------------------------
Sending Email

Server Type: SMTP

Server: smtp.gmail.com; Port: 587

Encryption method: SSL on a dedicated port 

Authetication
Type: login  
Username: *******@gmail.com

---

### Post by black veils on 2013-04-26
maybe it needs authentication to be same for incoming and outgoing, example: "login"

---

### Post by singlebinary on 2013-04-26
> **black veils said:**
> maybe it needs authentication to be same for incoming and outgoing, example: "login"

The login option under authentication does not exist for receiving email. The options for authentication are: 

Password
NTLM/SPA
GSSAPI
DIGEST-MD5
CRAM-MD5

Or is there something else you mean by "login"?

---

### Post by black veils on 2013-04-26
i misread, didnt see you had the equivalent of 'login' for both.

have you tried thunderbird instead? did you check the settings are correct? smtp port is 465.

---

### Post by singlebinary on 2013-04-26
> **black veils said:**
> have you tried thunderbird instead? did you check the settings are correct? smtp port is 465.

I do not want to install thunderbird as there is NO development on it. They will only be security updates. Geary has the same issue. That leaves me with Evolution. It's sad there isn't any good mail client in Linux.

Yes, I followed the setting from another post on Evolution + Gmail. Will search more for this.

---

### Post by black veils on 2013-04-27
there is also sylpheed and claws, i have tried both, sylpheed is what i use. claws didnt auto-fill addresses when creating mail, and there was another issue.

i can help you with setup for notification, or you could install ppa, which i recently did, that has a notification setting.

you haven't blocked those ports with a firewall have you?

---

