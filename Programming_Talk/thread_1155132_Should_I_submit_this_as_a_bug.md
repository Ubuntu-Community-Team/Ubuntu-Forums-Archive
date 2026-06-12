---
title: "Should I submit this as a bug?"
date: 2009-05-10
forum: Programming Talk
---

### Post by cl333r on 2009-05-10
I noticed that if (in a folder) 2 symbolic links exist pointing to each other then nautilus crashes (segmentation fault) right away. Thunar doesn't.

Should I submit it? To launchpad I guess?

If so, can it also be viewed as a security bug since it's so easy to replicate and doesn't require root privileges?

to replicate, in terminal:
ln -s link1 link2
ln -s link2 link1
now open nautilus and go to the dir where you created the sym links.

---

### Post by Bodsda on 2009-05-10
Just tested and can confirm this, I would submit it as a bug yes

---

### Post by nvteighen on 2009-05-10
Definitely, it's a bug... Though that situation is stupid enough, at least Nautilus should treat it in some way it doesn't crash (whatever, a message dialog giving you the option to delete one of the links...). Yes, Launchpad is a way to get heard.

---

### Post by cl333r on 2009-05-10
thanks!

UPDATE:
There was a bug on this reported a year or two ago and marked as "invalid" so I reopened it (as "confirmed"):

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/247644](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/247644)

---

### Post by heindsight on 2009-05-10
> **cl333r said:**
> thanks!

UPDATE:
There was a bug on this reported a year or two ago and marked as "invalid" so I reopened it (as "confirmed"):

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/247644](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/247644)

That bug report was marked invalid because I filed it with insufficient
information. I subsequently refiled as [https://bugs.launchpad.net/bugs/247921](https://bugs.launchpad.net/bugs/247921)

---

### Post by cl333r on 2009-05-10
Oops, alright, I noticed the bug dates back from 2008, I thought it's an easy to fix one.

---

