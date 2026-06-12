---
title: "What is equivalent to /etc/modprobe.d/aliases  ??"
date: 2017-09-07
forum: New to Ubuntu
---

### Post by m3atwad on 2017-09-07
Hello,

I"m new and I'm trying to bind two ethernet ports for fail over recover, mode "active-backup 1" in this tutorial:

[http://www.informit.com/articles/article.aspx?p=1381888&seqNum=3](http://www.informit.com/articles/article.aspx?p=1381888&seqNum=3)

I can't seem to figure out how to accomplish the equivalent of:

> open /etc/modprobe.d/ aliases, scroll to the bottom of the file, and add

```
alias bond0 bonding
options bonding mode=1 miimon=100
```

I'm using ubuntu 16.04.3 LTS code name xenial. 

Do I need to create the aliase file or am I missing something?  Is this confusion due to the newer version of Ubuntu I'm using?  Any direction is helpful thanks!

---

### Post by giglok on 2017-09-12
I had the same problem and found solution here: [http://ktecblog.blogspot.com/2017/09/where-is-etcmodprobedaliases-in.html](http://ktecblog.blogspot.com/2017/09/where-is-etcmodprobedaliases-in.html)

System loads all .conf files form /etc/modprobe.d/
Just create /etc/modprobe.d/aliases.conf and put your aliases in it.

---

