---
title: "What gets reported to Admin?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by garyed on 2008-04-29
I was setting up my wife as a user on one of my computers & when I tried with her as user using sudo & her password I got a message saying ".. will be reported to the Admin.." I realized that she doesn't have admin priviliges so I understand that but where would I look as Admin to find what was reported? Also using if she uses sudo again it doesn't give the prompt so I was wondering if there are only certain tasks that get reported.

---

### Post by freebeer on 2008-04-29
With regards to the second item, Ubuntu remembers the password for a period of time (10-15 minutes? it's configurable).  So if you issued a sudo (plus password) then do so again within the time period, you won't be prompted for a password.

I'm not at my Ubuntu machine to be able to answer your first question... I imagine it's in the /var/logs area, if you want to root around there for a likely candidate.

---

### Post by garyed on 2008-04-29
> **freebeer said:**
> With regards to the second item, Ubuntu remembers the password for a period of time (10-15 minutes? it's configurable).  So if you issued a sudo (plus password) then do so again within the time period, you won't be prompted for a password.

I'm not at my Ubuntu machine to be able to answer your first question... I imagine it's in the /var/logs area, if you want to root around there for a likely candidate.

Thanks for the reply,

I've tried searching /var/log directory but came up empty.
Besides not being able to find the report that was supposedly sent, I was also trying to figure out if reports get sent to the admin without the user being prompted too.

---

### Post by spiderbatdad on 2008-04-29
I would have bet on /var/log/messages
There is also system>>administration>>system log...auth_log...etc.

---

### Post by Oldsoldier2003 on 2008-04-29
> **garyed said:**
> Thanks for the reply,

I've tried searching /var/log directory but came up empty.
Besides not being able to find the report that was supposedly sent, I was also trying to figure out if reports get sent to the admin without the user being prompted too.

Usually what happens (if you have mail set up) is the admin user account receives a system email that says user soandso attempted to use sudo without privileges. No big deal since basically you told on yourself and you already knew :)

---

### Post by garyed on 2008-04-29
> **spiderbatdad said:**
> I would have bet on /var/log/messages
There is also system>>administration>>system log...auth_log...etc.

There is a lot of stuff in messages that shows who has logged on & info that I don't understand. I didn't see anything that looked like an alert but it may just be that it is showing an alert & I don't know what all the messages mean.

---

### Post by Monicker on 2008-04-29
> **garyed said:**
> There is a lot of stuff in messages that shows who has logged on & info that I don't understand. I didn't see anything that looked like an alert but it may just be that it is showing an alert & I don't know what all the messages mean.

I believe it should be in /var/log/messages

```
grep sudoers /var/log/messages
```

---

