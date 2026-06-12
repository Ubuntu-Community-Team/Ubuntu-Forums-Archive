---
title: "file sharing Ubuntu laptop Ubuntu PC"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by appoloin on 2008-07-07
Another question. I just installed ubuntu on my laptop and i want to share file from my PC to my laptop. both using Ubuntu. could anyone tell me how please?

---

### Post by hyper_ch on 2008-07-07
the simplest way IMHO is

(1) install ssh server
```

sudo apt-get install openssh-server

```
on the machine you want to log in to

(2) get a sft/scp capable program and use it to connect to it with the username and password that you use to normally login.

I like Konqueror for that (as I can split the window into multiple panes) and enter:  fish://remote_user@remote_computer


OR you can also mount the remote system into your filesystem with "sshfs"

---

