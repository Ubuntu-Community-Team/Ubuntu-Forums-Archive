---
title: "Problems with Thunderbird and Firefox..."
date: 2014-01-20
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-20
First off, I'll say I **am** paranoid. I just wiped my last (I hope) copy of Windows and moved to Ubuntu. I am having symptoms of a problem I don't understand. I am trying to send email. I keep being told to check my server settings, and they seem normal: Correct addresses, Inbound=Port 995, Outbound=Port 465. I tried several more times and it kept asking for another password. I checked my password, and it was correct. So, I decided to go online and check my password. Firefox, for three days now, has said it cannot connect to [http://www.att.net](http://www.att.net). I cannot check my password to see if it works on att.net. What do I do?:mad:
EDIT: The problem has resolved itself. How do I put "[SOLVED]" on the post?

---

### Post by The Cog on 2014-01-20
What program are you using to send email?
Scrub that - didn't read the title. Doh!

Can you ping [www.att.net?](www.att.net?)

If so, do you get lots of html output, or an error message when you type this command?
```
GET http://www.att.net
```

---

### Post by bc.haynes on 2014-01-20
The problem was I was using https:/ and not http:/. I don't know what ping is or how to do it.

---

