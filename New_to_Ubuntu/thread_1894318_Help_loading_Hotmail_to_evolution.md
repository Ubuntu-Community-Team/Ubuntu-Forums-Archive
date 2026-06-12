---
title: "Help loading Hotmail to evolution"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by SUperougi on 2011-12-12
I have yahoo mail loaded to evolution, that was easy following directions in the forum, I need hotmail also. Thanks:confused:

---

### Post by jaimeaux on 2011-12-12
Actually, I've done this before, but it takes a little bit of work. The most difficult part is just getting each individual part of it right (i.e. server name, ports, authentication). I've done it in evolution.... try looking it up on fedora forums (as I had asked it when I used Fedora), or here:
 
[http://jaimeaux.wordpress.com](http://jaimeaux.wordpress.com)
 
(Note: The above link is a reference for use w/ KMail, but it should be rather close.)
 
A lot of people will tell you to install additional software. Don't listen, it's not needed. I've been told to install some "hotwayd" or other software, it does nothing.
 
If you put in the right server, and the right ports, it will work.

---

### Post by SUperougi on 2011-12-12
I tried your settings, no go, must be missing something.

---

### Post by gandaran on 2011-12-12
> **SUperougi said:**
> I tried your settings, no go, must be missing something.
hotmail on evolution is easy to configure as evolution does almost everything when you enter a hotmail account, you just have to be careful pop server is selected and most important on username box enter the full hotmail account name, it will not work with just the username.
[https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

---

### Post by rushikesh988 on 2011-12-12
if everything fails try configuring evolution manually with outlook setting if ur friend have

---

### Post by jaimeaux on 2011-12-12
> **SUperougi said:**
> I tried your settings, no go, must be missing something.
 
 
This was a response that somebody posted on fedora forum a few years back after I was asking the same thing:
 
[http://forums.fedoraforum.org/showthread.php?t=224598](http://forums.fedoraforum.org/showthread.php?t=224598)
 
Try this?

---

### Post by N00b-un-2 on 2011-12-12
Dude, hotway/hotsmtp hasn't been necessary since like 2008.  Configure evolution as follows:

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
Server: smtp.live.com:587
Tick the box Server requires authentication
Security: TLS encryption
Authentication: PLAIN
Username: [email]username@hotmail.com[/email]
Tick the box remember password.

---

### Post by SUperougi on 2011-12-13
OK, will try these, at work now, will do these and see what happens. Thought I almost had it because it was asking for the password to the account, but the password didn't work. It was the right password. Thanks for help, all!

---

### Post by SUperougi on 2011-12-14
Thanks to everyone for their help. Since the suggestions did not work, I have decided to drop this and use Thunderbird instead.

---

### Post by jaimeaux on 2011-12-14
> **SUperougi said:**
> Thanks to everyone for their help. Since the suggestions did not work, I have decided to drop this and use Thunderbird instead.
 
 
.... Why don't you just use the port settings from thunderbird? you can probably view it in the options...

---

### Post by SUperougi on 2011-12-14
After looking at the various ways and trying the most reasonable I still got nowhere. I then taked to My son who is quite proficiant in these matters I went to Thunderbird and took about 20 seconds to set up my Yahoo account which took 2 hours with evolution and then it still didn't work right. I have to many other projects to use up time on this issue. Sometimes you have to admit defeat and go to another more easily won battle.
Thank you for your help. I hpe iin the future you will feel free to help on some other issue.

---

