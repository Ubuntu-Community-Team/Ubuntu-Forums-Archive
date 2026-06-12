---
title: "Ubuntu Software Centre not showing reviews"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by jaded247 on 2014-01-10
Hi, why is Ubuntu Software Centre not showing reviews and how do I fix it? 
It says 'No network connection. Connect to the Internet to see more reviews'. I can install software and the computer is connected to the internet. It's Ubuntu 13.10 64-bit.

I tried this, but still can't see reviews?
```
killall software-center
killall -KILL software-center
cd ~/.config && rm -r software-center
sudo apt-get update
sudo apt-get --purge --reinstall install software-center
```

---

### Post by +jacek+ on 2014-01-10
Same here - since yesterday. Looks like a new bug. Also [COLOR=#000000]Ubuntu 13.10 64-bit.

edit: maybe something with openssl???[/COLOR]

---

### Post by Buntu Bunny on 2014-01-10
Same for me. In fact, every time I open software centre I get a crash error

> The application Ubuntu Software Centre has closed unexpectedly.

Details
software centre has crashed with ValueError in_strptime(): time data '2013-04-12T01:15:;08:007Z' does not match format '%Y-%m-%d %H:%M:%S'

---

### Post by vasa1 on 2014-01-11
Till it's fixed maybe [https://apps.ubuntu.com/cat/](https://apps.ubuntu.com/cat/) will do?

---

### Post by DuckHook on 2014-01-11
Just filed launchpad bug report [Bug #1268186]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1268186")

Please add your results and confirmation to above bug report.

---

### Post by Roo8choo on 2014-01-12
Another bug report on launchpad right here: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1268250](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1268250).
Also a user named Matthew Palermo made a fix for the problem, it works for me :D.

Greetings,

Allard

---

