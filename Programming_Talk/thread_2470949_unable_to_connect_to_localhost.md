---
title: "unable to connect to localhost"
date: 2022-01-17
forum: Programming Talk
---

### Post by Tom_Carr on 2022-01-17
I am trying to set up a mysql database using mysql workbench.  I set up a new connection according to instructions in a youtube video.  When I test the connection I get:

"Failed to connect to mysql at 127.0.0.1:3306 with user root.  unable to connect to localhost"

How do I fix this?

I am a hobbyist programmer, not a professional.

---

### Post by TheFu on 2022-01-18
Is mysql actually running?

---

### Post by Tom_Carr on 2022-01-18
You can ignore my question.  I installed SQLite.  It was quick and easy to install and does everything I need.

---

### Post by TheFu on 2022-01-18
> **Tom_Carr said:**
> You can ignore my question.  I installed SQLite.  It was quick and easy to install and does everything I need.

SQLite has some issues that may or may not be important.  For example, all data is stored as text.  Dates, integers, whatever - -are internally stored as text.  That's 1 less validation check in a DB.  I use SQLite for my low-volume blog, so clearly, I've decided for some things, it is very useful. Just depends on the use.  Best to be informed and choose to accept the issues.

---

