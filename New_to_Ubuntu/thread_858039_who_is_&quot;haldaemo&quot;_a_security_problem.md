---
title: "who is &quot;haldaemo&quot;? a security problem?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-13
I just installed Htop which allows me to see all the running process and details. In the "User" column, it's mostly my name and root, but there is a user "haldaemo", who the hell is this guy? I see its command directory is /usr/sbin/hald

?????? wish anybody tell me this is normal???????? Please! I'm a single PC at home, no networking, I didn't add any other user after install.

---

### Post by hyper_ch on 2008-07-13
have you tried to find out what it is yourself?

---

### Post by brian_p on 2008-07-13
> **imjscn said:**
> I just installed Htop which allows me to see all the running process and details. In the "User" column, it's mostly my name and root, but there is a user "haldaemo", who the hell is this guy? I see its command directory is /usr/sbin/hald

I think you mean 'haldaemon'

> ?????? wish anybody tell me this is normal???????? Please! I'm a single PC at home, no networking, I didn't add any other user after install.

It's normal.

```
man hald
```

---

### Post by mcduck on 2008-07-13
it's HAL daemon, (HAL being short for Hardware Abstraction Layer).

[http://en.wikipedia.org/wiki/Hardware_abstraction_layer]("http://en.wikipedia.org/wiki/Hardware_abstraction_layer")

(In Linux, Unix and other true multitsking operating systems programs running in background, often as their own users, are often called "daemons". Not the same thing as demon in christian religion.. ;))

---

