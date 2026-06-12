---
title: "Upgrading Squid installed with apt-get"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Gravidar on 2008-09-29
Hi, I've installed Squid Proxy Server to accelerate Apache on a VPS with 128MB RAM but apt-get installed version 2.6 and not 3.0 (I need the new logformat directive). 

I've done:
```
apt-get update
apt-get upgrade
```
but Squid is not in the list. can I download a new version of Squid onto the server somewhere and use apt-get to upgrade it or do I have to uninstall 2.6 and compile 3.0 myself?

All help appreciated, I hope that's enough info to describe the issue.

Cheers

---

### Post by nowshining on 2008-09-29
pretty much compile 3.0 urself unless they have a deb, etc...

---

### Post by bodhi.zazen on 2008-09-29
I would remove 2.6 (with purge) and compile 3.0

```
sudo apt-get remove --purge squid
```

---

### Post by jemate18 on 2008-09-30
compilation of the 3.0 is adviced.....

---

### Post by Gravidar on 2008-10-01
Thanks for the replies.
Squid 3.0 doesn't exactly come ready-to-bake for Ubuntu so I had to get very friendly with the compile options and config files. This is of course after having to learn how to compile something in the first place and when you don't have a C compiler installed it's a very steep learning curve indeed!

But ... got there in the end (after 2 days!) and now have an accelerated Apache web server, let's hope it does what it's supposed to :)

time for a beer me thinks

Cheers

---

### Post by bodhi.zazen on 2008-10-01
> **Gravidar said:**
> Thanks for the replies.
Squid 3.0 doesn't exactly come ready-to-bake for Ubuntu so I had to get very friendly with the compile options and config files. This is of course after having to learn how to compile something in the first place and when you don't have a C compiler installed it's a very steep learning curve indeed!

But ... got there in the end (after 2 days!) and now have an accelerated Apache web server, let's hope it does what it's supposed to :)

time for a beer me thinks

Cheers

Congratulations, sounds like quite the project.

If you have the time or interest, considering posting the solution ;)

---

