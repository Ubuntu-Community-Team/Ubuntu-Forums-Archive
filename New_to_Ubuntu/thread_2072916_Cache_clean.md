---
title: "Cache clean?"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by will1982 on 2012-10-18
I know Ubuntu builds caches, is there any way to get rid of them?

---

### Post by Lisiano on 2012-10-18
You mean updates? Fire up a terminal (Ctrl+Alt+T) and type in ```
sudo apt-get clean
```That will delete everything in your apt cache (Old installers so to say).

---

### Post by jerrrys on 2012-10-18
> **will1982 said:**
> I know Ubuntu builds caches, is there any way to get rid of them?

maybe one

[https://wiki.ubuntu.com/ReducingDiskFootprint](https://wiki.ubuntu.com/ReducingDiskFootprint)

---

### Post by newb85 on 2012-10-18
Which caches are you trying to clean?

---

### Post by buckyaustin on 2012-10-18
Install bleachbit, this cleans all the unnecessary files in Ubuntu.

"sudo apt-get install bleachbit"

Then run it and click as many boxes as you can. Delete them. That should get rid of every cookie.

---

### Post by will1982 on 2012-10-18
> **newb85 said:**
> Which caches are you trying to clean?

All of them.

---

### Post by will1982 on 2012-10-18
> **buckyaustin said:**
> Install bleachbit, this cleans all the unnecessary files in Ubuntu.

"sudo apt-get install bleachbit"

Then run it and click as many boxes as you can. Delete them. That should get rid of every cookie.

Ah bleachbit helped a lot, thanks :)

---

### Post by buckyaustin on 2012-10-19
Please mark the thread as solved. Also happy to help. Why did you want to clean the cache anyway?

---

### Post by AlexDudko on 2012-10-19
System settings > Privacy.

---

