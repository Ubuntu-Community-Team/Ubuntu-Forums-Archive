---
title: "Setting Up Evolution for a Gmail Account"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by drsaamah on 2008-04-26
So all my time with Ubuntu, and I still haven't used Evolution.  I was thinking of trying it out, but I have no idea how to set it up.  I tried guessing on all the fields but that didn't work.  So if I have gmail account, could someone guide me through the set up process?  Like the POP versus Hub stuff or security type or whatever... hehe.  I don't know much about this, sorry.  Thanks in advance!

---

### Post by Tabenx on 2008-04-26
Basically, start the evolution wizard (when it first starts) and enter the following when so instructed:
incoming: imap.gmail.com  (put a check in the SSL box)
outgoing: smtp.gmail.com (put a check in the TLS box)
and of course enter the correct account information throughout the process. Post back if i missed anything, i'll be watching the thread.

---

### Post by drsaamah on 2008-04-26
Whats the "Server Type"?

---

### Post by Tabenx on 2008-04-26
The server type is IMAP and for outgoing is SMTP.
Edit:
Oo, looks like i forgot the evolution wizard. Let me start over.
For Recieving Mail:
Server type: IMAP
Server: imap.gmail.com
Encryption: SSL
Hit Next
Sending Mail:
Server Type: smtp
Server: SMTP.gmail.com
Use Secure Connection: TLS

---

### Post by drsaamah on 2008-04-26
Hmm... I don't know what's wrong.  When i click on "Send/Receive" after the set up, it just doesn't work.  Oh well, its kind of late.  I'll try again after a bit of a nap. Thanks for your help!

---

### Post by gandaran on 2008-04-26
a complete guide
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

---

### Post by drsaamah on 2008-04-26
Thanks guys, this definitely helped.  Hopefully others can use your advice as well!
...
...
uh, how do you mark a thread as "Solved" now?  The option seems to have disappeared...

---

