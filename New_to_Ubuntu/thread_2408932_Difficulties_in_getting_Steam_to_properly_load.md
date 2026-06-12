---
title: "Difficulties in getting Steam to properly load"
date: 2018-12-25
forum: New to Ubuntu
---

### Post by noitseuq on 2018-12-25
(I'm new to both Ubuntu and this forum, so if this is the incorrect place for my question do tell me.)

Okay, so I've been trying to get Steam to work for about an hour or two, and nothing seems to be working. I have installed through the Terminal, using 

sudo apt-get install steam

and it installed, but whenever I try to open it it responds with this error message:

You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6

I then tried the following commands to retrieve the missing file

sudo apt-get update
sudo apt-get install libc6-i386
(The above is from: [https://askubuntu.com/questions/602637/you-are-missing-the-following-32-bit-libraries-and-steam-may-not-run-libc-so-6/602642](https://askubuntu.com/questions/602637/you-are-missing-the-following-32-bit-libraries-and-steam-may-not-run-libc-so-6/602642)), but the same error still shows up.
I am perplexed and do not know what to do. How do I fix this?

---

