---
title: "User problems"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by BornABrokenMan on 2012-12-09
Top right says I'm logged into 'Jim'

open up terminal and it says jack@ubuntu

and when I open up system terminal everything in the user column has Jack there.

I can't access Root, and many other things because I don't have the permissions on Jim, even though it's the only account and an Administrator account.

Someone please show me the way

---

### Post by papibe on 2012-12-10
Hi BornABrokenMan. Welcome to the forums ):P

Could you post the result of this commands?
```
id

groups

grep -i jim /etc/passwd

grep -i jack /etc/passwd
```
Regards.

---

### Post by DuckHook on 2012-12-10
> **BornABrokenMan said:**
> Top right says I'm logged into 'Jim'

open up terminal and it says jack@ubuntu

and when I open up system terminal everything in the user column has Jack there.

I can't access Root, and many other things because I don't have the permissions on Jim, even though it's the only account and an Administrator account.

Someone please show me the way

It is likely that when you installed Ubuntu, you typed in "Jim" when it asked you for the "full name" of the user and then typed in "jack" when it asked you for "username". The two are not the same.

The system is recognizing your "usename" as "jack". The name displayed on the upper right corner is not relevant to Ubuntu.

Are you using *sudo* to make system changes?

EDIT:

@papibe's commands will show you which name the system considers your username. It will also show if you belong to the administrator account. Please post results.

---

