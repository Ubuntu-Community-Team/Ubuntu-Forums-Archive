---
title: "Python Help"
date: 2008-12-18
forum: Programming Talk
---

### Post by Swenghk on 2008-12-18
I was writing a script in Python and I need to know how to return to the top of a conditional statement without using the "continue." For example:

```
security = 0
username = ""
while not username:
    username = raw_input("Username: ")

password = ""
while not password:
    password = raw_input("Password: ")

if username == "seth" and password == "allen":
    print "Welcome, Seth. Security level 5"
    security = 5
elif username == "guest" and password == "guest":
    print "Welcome guest. Security level 1"
    security = 1
else:
    print "Invalid login..."
```

I want to know how to return to the "Username: " prompt if you get an invalid login. Thanks!

---

