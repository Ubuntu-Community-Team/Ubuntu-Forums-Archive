---
title: "XAMPP stopped working."
date: 2008-07-14
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-07-14
I usually start up XAMPP through the control panel and just click Start at the top and it all works and when I got to [http://localhost.com/name](http://localhost.com/name) it works and I can see my files. Well today it stopped working and when I start it they all start except ProFTPD and now I cannot access localhost or anything. Is there a way to fix this?

---

### Post by cariboo on 2008-07-14
Open up a Applications-->Accessories-->Terminal and type:

```
cat /etc/hosts
```

Post the output in your next post.

Jim

---

### Post by ImThatNerd on 2008-07-14
```
ryan@ryan-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	ryan-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ryan@ryan-desktop:~$ 





```

I currently have XAMPP 'stopped'.

---

### Post by ImThatNerd on 2008-07-14
Anyone?

---

### Post by ImThatNerd on 2008-07-14
cariboo907 can you help? This is sort of urgent.

---

### Post by ImThatNerd on 2008-07-15
Hopefully luck after 4 hours.

---

