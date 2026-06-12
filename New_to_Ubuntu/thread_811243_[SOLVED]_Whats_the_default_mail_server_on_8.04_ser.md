---
title: "[SOLVED] Whats the default mail server on 8.04 server edition?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by cackles on 2008-05-28
Hi, quick question about the 8.04 server when you are setting it up. Where you get the choice of LAMP, SSL, Samba etc. to install during setup what is the mail server it would install under those conditions, is it Postfix?

I had a quick search and in the howtoforge perfect setup guide, which seems to be popular, they tell you how to install Postfix. The problem being, in my head, the method uses apt-get. I would have thought you wouldnt have needed to do that if you selected it during setup or are these just additional modules to take it from basic to secure?

```
apt-get install postfix libsasl2-2 sasl2-bin libsasl2-modules procmail
```

---

### Post by bluefrog on 2008-05-29
mail server is postfix

---

### Post by cackles on 2008-05-29
Thanks, does the apt-get line I posted install postfix and its modules or just modules for it though or is that the the actual line for postfix?

---

