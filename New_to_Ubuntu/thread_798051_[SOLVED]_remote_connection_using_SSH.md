---
title: "[SOLVED] remote connection using SSH"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by ptn107 on 2008-05-17
Situation:
-Desktop running Ubuntu with the necessary SSH packages installed.
-Laptop running Debian (testing) also with the SSH stuff installed.
-Both machines can ping each other on the internal net.

I can connect* to the laptop (Debian) from the desktop (Ubuntu), however when trying the other way around (laptop to desktop) the connection times out with:
```
ssh: connect to host 192.168.24.101 port 22: Connection timed out
```

I just can't figure out why.  Suggestions?

*I'm trying to connect one to the other on my home network so the firewall shouldn't be an issue right?

---

### Post by ptn107 on 2008-05-17
UPDATE: The physical router/firewall wasn't affecting the connection.  However, Firestarter on the Ubuntu machine was the culprit.

---

### Post by Thirtysixway on 2008-05-17
Perhaps your ssh daemon isn't running for some reason.  Try running
```

ps aux | grep ssh

```

If ssh isn't running, run
```

/etc/init.d/ssh start

```

---

