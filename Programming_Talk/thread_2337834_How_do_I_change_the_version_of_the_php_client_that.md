---
title: "How do I change the version of the php client that is running?"
date: 2016-09-22
forum: Programming Talk
---

### Post by AbDk38H on 2016-09-22
I currently have several versions of php installed. 5.6, 7.0 and 7.1RC. I am able to switch between the various versions that apache uses but when I type "php --version" on the command line, I always get the answer: 7.1RC. My question is, how to I change the client version that is running (to 5.6)?

---

### Post by AbDk38H on 2016-09-22
found the answer:sudo ln -sfn /usr/bin/php5.6 /etc/alternatives/php

---

