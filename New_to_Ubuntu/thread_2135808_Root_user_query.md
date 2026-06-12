---
title: "Root user query"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by awatkins1971 on 2013-04-15
Is it possible to view are change another user activity etc. i.e someone has gone home and is still log on, In Root can you log them out, etc. without knowing their password? Thank you in advance :cool:

---

### Post by sp-1070 on 2013-04-15
sudo pkill -KILL -u username

Very brute force stuff as this will kill all the users processes but itl log them out alright

---

### Post by grahammechanical on 2013-04-15
Do we need a password to log someone out?

---

### Post by awatkins1971 on 2013-04-15
thanks as I'm new to Linux, just wondering, how things are done.

---

### Post by sp-1070 on 2013-04-15
yes thats where the sudo comes in,
you see annyone in the sudo file is like a super user.
Sso when you type a command with sudo in front of it its like run as an administrator in windows

---

