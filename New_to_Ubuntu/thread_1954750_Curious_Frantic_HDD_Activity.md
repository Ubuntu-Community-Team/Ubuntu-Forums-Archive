---
title: "Curious Frantic HDD Activity"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2012-04-08
I am running Lubuntu 10.04 on a Dell L400/800MHz/256Mb laptop.  All is running well until about 5-10 minutes after boot up when the HDD activity light suddenly starts indicating _frantic_ HDD activity with attendant slowing up of the laptop.  This continues even with no applications except desktop open.  This activity slowly subsides over the next 10-15 minutes.  I attach two screen shots to indicate the level of activity.
What is causing this and is there a solution?

---

### Post by ajgreeny on 2012-04-08
Something apears to be using a lot of cpu for a python script  activity of some kind.  ```
ps aux | grep python
```may help you find out what could be causing the problem; in my case it is very occasionally gmail-notify.

---

### Post by Dumpy Dumpster on 2012-04-09
Good Morning, ajgreeny, and thanks for your reply.  I attach a screenshot of my terminal.  The first entry is just after start up in the calm period and the rest are during the frantic stage.
It seems to me the problem is an 'update of xapian-index'.
What is it, is it vital and can it be turned off?

---

### Post by ajgreeny on 2012-04-09
See [http://ubuntuforums.org/showthread.php?t=1062688](http://ubuntuforums.org/showthread.php?t=1062688) for a probable solution.

---

### Post by Dumpy Dumpster on 2012-04-09
Thanks again, ajgreeny, have just read through your link.  Will get on to it tomorrow PM and get back to you.

---

### Post by Dumpy Dumpster on 2012-04-10
I have followed Eiríkr's solution in post number #8 of [http://ubuntuforums.org/showthread.php?t=1102483]("http://ubuntuforums.org/showthread.php?t=1102483")
This has the advantage that I ( being a very simple Linux user) can reverse it if needed!
The problem has now been fixed.
So many thanks again to ajgreeny and also to Eiríkr

---

