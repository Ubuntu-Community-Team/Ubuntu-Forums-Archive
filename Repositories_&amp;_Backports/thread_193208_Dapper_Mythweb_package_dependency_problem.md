---
title: "Dapper Mythweb package dependency problem"
date: 2006-06-09
forum: Repositories &amp; Backports
---

### Post by speedsix on 2006-06-09
I'm not sure if this is the correct forum but..

The 'mythweb' package needs to install 'php4-mysql' or it won't work. It's not listed as a dependency.

Also, the 'mythtv' package creates a mythtv user but afaik doesn't let you in on what it's password is?


Dom

---

### Post by Philip g on 2006-09-29
You can set the password of a user by logging in as the user you created upon first installing and typing:-

sudo passwd username

in the case of the mythtv user:-

sudo passwd mythtv
(you will be asked for your password if you have not used sudo for a bit)
(then the new password for the user mythtv) 
(then a confirmation of this new password)

Although I am sure you have sorted this my now, I thought I could post anyway in case others came across this thread.

---

