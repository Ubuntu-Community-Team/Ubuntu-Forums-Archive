---
title: "trying to uninstall postgres sql, but I don't remember the password"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by elgrbggmail.com on 2013-09-29
Hi! I'm very new to linux, so I hope you can bear with me.

I installed postgres sql for use in my Ruby on Rails app (that I'm deploying to Heroku). I'm having a hard time setting it up, so I want to uninstall postgres and reinstall it. However, when I try to uninstall it (sudo apt-get remove postgres), it asks me for my password. I unfortunately do not know what it is, as I tried many different things when setting it up. Is there a way to uninstall postgres without the password?

Thanks!

---

### Post by The Cog on 2013-09-29
It's the same password you use as you log in. It's just checking that you are you and not someone else while you are away getting a coffee.

---

### Post by elgrbggmail.com on 2013-09-29
Thanks! However, I tried putting in my password, and it told me "Sorry, try again"

---

### Post by elgrbggmail.com on 2013-09-29
Also, it asks me this: [sudo] password for postgres: 
But my username is not postgres!

---

### Post by The Cog on 2013-09-29
How are you trying to remove it?

---

### Post by elgrbggmail.com on 2013-09-29
sudo apt-get remove postgres

---

### Post by The Cog on 2013-09-29
Yes, that's how I would do it. 
But I've never installed or removed postgres and don't know what that other prompt is all about. It is not something I would have expected to see.
Hopefully someone familiar will be able to help. Sorry.

---

### Post by elgrbggmail.com on 2013-09-29
Well, I should have thought of that sooner! I restarted, and then tried the same command, and this time it asked for MY password - for my username. Problem solved!
Thanks for your help.

---

### Post by zia.newversion on 2013-09-30
Seeing as this thread is marked solved, there's probably no cause for me to trot here.
However, I am still curious. Why would [FONT=courier new]sudo[/FONT] or [FONT=courier new]apt[/FONT] do that?

---

### Post by elgrbggmail.com on 2013-09-30
No clue! I'd also love to know, so I guess we'll see if anyone answers you...

---

### Post by SeijiSensei on 2013-09-30
The "postgres" user owns the PostgreSQL installation.  Usually the only way one can become the postgres user is by using "sudo su postgres".  You cannot log in as this user as it has no password, so you must have used a procedure similar to what I just described to become that user.  Naturally the postgres user has no sudo rights.

---

