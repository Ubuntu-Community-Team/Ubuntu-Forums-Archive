---
title: "Evolution - Error Failed to read a valid greeting from POP server"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by cwmoser on 2014-01-09
I attempted to install Ubuntu 13.10 in another partition from my workhorse 12.04.
Well, 13.10 froze after I logged in.

I rebooted back to my old 12.04 and now I get an orange Evolution error
when I press the Send/Receive button:
[B]Error while Fetching Mail.
Failed to read a valid greeting from POP server pop.gmail.com
[/B]
Evolution had been pretty solid until I tried to install 13.10 in a separate partition.
I have:
[B]/dev/sda1 = 13.10
/dev/sda4 = 12.04
/dev/sda3 = /home
[/B]

Carl

---

### Post by cwmoser on 2014-01-10
I fixed this error this way.
- removed ~/.evolution
- sudo  apt-get purge evolution
- went to Software Center and installed evolution
- re-setup my 2 email accounts.

Now I have a working Evolution 3.4.2

---

