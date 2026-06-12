---
title: "[SOLVED] Thunderbird with gmail - can't connect to pop server"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by szucslaszlo on 2008-08-26
Hello there!

I have just switched to Ubuntu Hardy Heron, and wished to use my gmail account with Thunderbird - just as I have done this before, on a Windows system. Problem is, that while on Windows, I didn't have to manually configure Thunderbird, yet under Ubuntu it is a must. I have found, that google's pop server address is pop.gmail.com - but it won't work for some reason. I can sign in from the web, but not from Thunderbird. My POP access is turned on, and I can even send letters from the account.

I didn't find a thread with the same problem, only similar ones in the archives, but they all have a common starting-point: the users managed to make Thunderbird actually work, under their Ubuntu system, and after a while it suddenly stopped connecting to the gmail server. I have absolutelly no idea what might be the problem, please help me.

Many thanks!

---

### Post by jgrabham on 2008-08-26
you need to change the ports from what thunderbird has as default, to what google needs, the details are [HERE]("http://mail.google.com/support/bin/answer.py?hl=en&answer=13287").

---

### Post by halitech on 2008-08-26
I've been using gmail with thunderbird for almost 2 years and no problems with it at all once I set it up. 

first thing to do is make sure gmail is set up to allow pop access (which you say it is)

for the account settings:
Server Settings Tab:
Server Type: 	POP Mail Server
Server Name: 	pop.gmail.com
Port: 	995
User Name: 	(your Gmail username)
Use secure connection: 	SSL
Leave messages on server: 	disabled

for the outgoing I've always had to leave mine on my isp settings as they block port 25 and 587 :(

---

### Post by szucslaszlo on 2008-09-01
Thanks guys, I successfully configured my Thunderbird - using Thunderbird was my last connection with MS Windows, but I knew I would overcome this problem eventually:)

I kinda love my new Ubuntu system, though I messed it up a few times with a couple of sudo terminal commands, so I had to do some reinstalls...:P:) practica makes perfect. Thanks again!\\:D/

---

