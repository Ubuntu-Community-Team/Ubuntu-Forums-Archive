---
title: "how i can speed up my ubuntu software center"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by mastercode on 2013-07-19
when i have downloading  software in ubuntu software he told me waiting for apt-get to exit and he do that for ever :mad:

how i can skip from that and download my soft ware !!

---

### Post by su:bhatta on 2013-07-19
Were you installing the System Updates when you tried to download software from Ubuntu Software Center?

Only one resource can use apt-get at any given point of time... If you try to install say 3 applications from Ubuntu Software Centre then it is done one by one, i.e. not simultaneously ...

Waiting for apt-get to exit, means that the apt-get is already working & Ubuntu Software Center can use the apt-get function only when it gets free...

Here is a link from Ubuntu Help that gives basics of Package Management..

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

