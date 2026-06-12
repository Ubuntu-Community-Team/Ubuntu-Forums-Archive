---
title: "Problems connecting to GoogleTalk through Pidgin"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-10-03
Hey all, 

I've tried connecting to my Google Talk account through Pidgin but it won't connect. I've managed to connect with Msn and Facebook Chat, but not Google. 

Any ideas?

Thanks in advance

Chris

---

### Post by LowSky on 2008-10-03
I think I read there was a glictch or something with Googletalk in the current version of Pidgin.

You can get the latest at [http://www.getdeb.net/release.php?id=3140]("http://www.getdeb.net/release.php?id=3140")

---

### Post by AndyCooll on 2008-10-03
Google Talk is working fine for me. My settings are as follows:

Protocol: XMPP
Username: Yourusername
Domain: googlemail.com
Resource: Gaim
Password: blah blah blah

On the advanced tab:
Require SSL/TLS ticked
Connect port: 5222
Connect server: talk.google.com
File transfers: proxy.jabber.org

Obviously your settings may be different depending on how your Jabber/Google account is set up etc

:cool:

---

### Post by Ecclesia on 2008-11-05
I had the same issue and your suggested settings worked except that it wouldn't accept the domain: googlemail.com.  After playing around with it for a bit I discovered that gmail.com works.  Thanks for the rest of the info.  It's odd that the base Pidgin settings are so different from what you actually need.  In all my previous experience with Gaim/Pidgin it always worked fine with the defaults.

---

### Post by knowledgeispwr on 2008-11-14
AndyCooll, thanks for sharing your settings.  That's how I got GoogleTalk working for me, except the Domain for me is gmail.com.  Again, very weird that Pidgin's default settings aren't correct.

---

