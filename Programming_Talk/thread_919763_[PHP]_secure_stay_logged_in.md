---
title: "[PHP] secure stay logged in"
date: 2008-09-14
forum: Programming Talk
---

### Post by ELD on 2008-09-14
Basically for my small forum i need a way of doing a secure stay logged in feature with a cookie i am guessing.

Anyone know a good secure way of doing it?

---

### Post by Reiger on 2008-09-14
Maintain a SESSION table. Read up on PHP Session management in the php.net manuals.

---

### Post by ELD on 2008-09-14
The php manuals are not exactly helpful in building a stay logged in function, what i am looking for is a decent tutorial, php.net is too broad and basic.

---

### Post by drubin on 2008-09-14
I would suggest downloading phpbb3 and taking a look how they do it. It is pretty simple.

---

### Post by Phristen on 2008-09-14
How secure is "secure"?
Is saving a password hash and a login name in coookies secure?

---

### Post by drubin on 2008-09-15
NOT at all!

I could simply copy your cookie file to another computer and login as you.

The reason that forums/and others are safer is they only store the session ID and that can be checked against when it was created. original IP address....

---

### Post by ELD on 2008-09-15
> **rubinboy said:**
> NOT at all!

I could simply copy your cookie file to another computer and login as you.

The reason that forums/and others are safer is they only store the session ID and that can be checked against when it was created. original IP address....

So basically have a cookie storing the session id, stick the session id, timing and ip into database and check against that?

Although how would i check what time the cookie was made against the time in the database?

And also for 56k users whos ip changes on every dial in, it wouldn't work will it?

Doesn't sound too hard and sounds pretty secure, thanks for the push in the right direction.

---

### Post by drubin on 2008-09-15
Sorry for the brief reply.... I am currently at work. If you need further help just post a question and hopefully I will get back to you later.

Good luck :) 

also don't use a plain txt session id. or even a auto increment id. because then I could just up my id by one. 

ps that is how php session are done.

---

### Post by ELD on 2008-09-15
I am guessing md5'ing the session id into the cookie and into the database should do the trick?

But if i insert the time into the database, how do i check that time vs when the cookie was made? As checking against IP wouldn't work as peoples ip's change too much.

I appreciate any help :)

---

### Post by Phristen on 2008-09-16
> original IP address....And if I have a dynamic IP?

---

### Post by drubin on 2008-09-16
Normally Isp's give out IPs in a range of 192.168.X.X or something similar You could validate bassed on the first 2 groupings... 

Also how often does your dynamic ip change? 

ps these were only idea's of how to do things.

---

### Post by shulace717 on 2010-02-18
To further contribute:
 
You've mentioned issues with ip comparisons.  Examing the first few values of both the stored $_SESSION["ip_address"] and the new $_SERVER['REMOTE_ADDR'].
 
I've also seen the verification of the user agent.  A stored $_SESSION["user_agent"] verse the $_SERVER['HTTP_USER_AGENT'].
 
**Example of value:**
[I]$_SESSION[user_agent] = Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; WOW64; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR 3.5.21022; .NET CLR 3.5.30729; .NET CLR 3.0.30729)
[/I]

---

