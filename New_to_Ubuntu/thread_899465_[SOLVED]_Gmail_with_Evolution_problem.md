---
title: "[SOLVED] Gmail with Evolution problem"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by penguinszp on 2008-08-24
I'm having issues sending mail through gmail using Evolution. I can receive emails without a problem, but cannot seem to send.

I've tried several different things to try to fix it, but nothing has worked so far.

My settings in the 'Sending email' tab are as follows:

**Server Configuration**
Server type: SMTP
Server Configuration: smtp.gmail.com:465
Server requires authentication (yes)

**Security**
Use secure connection: SSL encryption

**Authentication**
Type: login
Username: ****@gmail.com


I have tried several different Server Configuration addresses like 
smtp.gmail.com, smtp.gmail.com:587, 72.14.247.109:465, smtp.gmail.com:465, and none of those has worked so far.

When I try to send mail, it takes a very long time, then eventually it gives me the error message saying it could not connect because the connection timed out. 

Now the really weird part here is that thus error mentions "Could not connect to mail.rpi.edu" (my other mail that I use with evolution) even though I am trying to send through gmail. I've checked it out and I definitely only use gmail to send out my messages, but if there is something I don't know about that I should about multiple email clients then please let me know. 

It also seems to have issue sending out only to certain people, as I've sent from my gmail account to my rpi account, and i've sent to an msn address successfully too!

I heard that there may be a problem with my port 25 being blocked, but i thought the ':465' at the end of the server configuration was a workaround for this?

This is really confusing me, any help is very much appreciated

---

### Post by knattlhuber on 2008-08-24
I remember that quite a few people had issues with the gmail/Evolution combination and some (including myself) eventually switched to Thunderbird

[http://ubuntuforums.org/archive/index.php/t-509193.html]("http://ubuntuforums.org/archive/index.php/t-509193.html")
[http://ubuntuforums.org/showthread.php?t=438999]("http://ubuntuforums.org/showthread.php?t=438999")
[http://ubuntuforums.org/showthread.php?t=697340]("http://ubuntuforums.org/showthread.php?t=697340")

---

### Post by halitech on 2008-08-24
most ISPs do block port 25 and depending on them, they may have blocked port 465 as well. Try port 587 instead

Edit: just seen you have tried port 587. maybe that is blocked as well. You may need to use your ISP instead of gmail to send email.

---

### Post by lswb on 2008-08-24
I use gmail with evolution. I do not have a port number in the server field, just "smtp.gmail.com" The encryption type is TLS, not SSL. Otherwise my configuration appears the same as you have posted. One other thing, make sure that evolution is not in offline mode. (If you are using Network Mangler^B^B^B^B^B^B^B Manager and your connection is through ppp or some other method that NM doesn't manage, evolution will start up in offline mode) Look for the little plug icon at the bottom left of the screen.

---

### Post by dje on 2008-08-24
there is a nice guide [here]("http://www.ubuntu1501.com/2007/11/using-evolution-with-gmail.html"), its always worked for me

dje

---

### Post by penguinszp on 2008-08-24
Problem solved! I switched my encryption type to TLS and ended up going with smtp.gmail.com:587 for my Server Configuration. 

One oddity was that the messages I had been trying to send over and over still didn't send after I had changed my settings, but went through immediately when i simply composed new messages and pasted the contents of the unsendables into them. Not sure what this means but as long as I can send without issue from now on I'm not going to let it bug me.

Thanks for all the help!

---

