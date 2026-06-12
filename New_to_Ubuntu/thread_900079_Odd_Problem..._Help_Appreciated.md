---
title: "Odd Problem... Help Appreciated"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by GreenLungz on 2008-08-25
So while Ubuntu has been treating me quite nicely for some time now, only just recently has it started to give me some issues. For starters Firefox is buggy as hell, crashing at random, and sites like Imeem.com are a no-go at all times. I'm thinking its a flash based issue? The screen also randomly fades out to black and white, and then back after a bit. 

Thats not my main issue though, whenever I try to install updates I get this error.
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by niccholaspage on 2008-08-25
Run sudo dpkg --configure -a like how it says.Tell me if this works.

---

### Post by HereInOz on 2008-08-25
Have you run sudo dpkg --configure -a in a terminal yet.  If you do, it may sort out your issues.
If it doesn't, post back.

---

### Post by maddog39 on 2008-08-25
Yea generally you should follow the directions as directed by the command output. As far as firefox is concerned, yea its very likely a flash issue but what version of Ubuntu/Firefox are your running. If your still running Firefox 2 its highly advised you upgrade to Firefox 3 as most if not all of the crashing problems (especially related to flash) have been eleviated.

---

### Post by GreenLungz on 2008-08-25
When I enter that code into the terminal this is what I get

```
Setting up java-common (0.28ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

As for Firefox I am running version 3.

---

### Post by GreenLungz on 2008-08-25
Yeah I feel like a tool, running that in Terminal fixed my issue with not being able to make updates and the like, however Firefox is still buggy as ever. Anyone got any ideas on how to fix that?

---

