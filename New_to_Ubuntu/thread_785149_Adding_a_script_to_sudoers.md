---
title: "Adding a script to sudoers"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by dmub82 on 2008-05-07
I want user "d" to be able to run a script, ~/Documents/Scripts/reconnect.sh, with sudo without entering a password (so I can schedule it to run without intervention). How do I set that up in my sudoers?

(I've got the basics of using visudo, I just can't figure out the exact syntax to do what I want.)

---

### Post by Xiong Chiamiov on 2008-05-07
Is [this]("https://help.ubuntu.com/community/RootSudo#head-66c2db5bdb2734f0a66336d8d68499c47c82fff5") what you're looking for?

---

### Post by kerry_s on 2008-05-07
> **dmub82 said:**
> I want user "d" to be able to run a script, ~/Documents/Scripts/reconnect.sh, with sudo without entering a password (so I can schedule it to run without intervention). How do I set that up in my sudoers?

(I've got the basics of using visudo, I just can't figure out the exact syntax to do what I want.)


**d ALL=NOPASSWD: ~/Documents/Scripts/reconnect.sh**

you might have to use full path, it would be better to put your script in /usr/local/bin

**sudo cp ~/Documents/Scripts/reconnect.sh /usr/local/bin/reconnect**

**d ALL=NOPASSWD: /usr/local/bin/reconnect**

---

### Post by dmub82 on 2008-05-07
> **kerry_s said:**
> **d ALL=NOPASSWD: ~/Documents/Scripts/reconnect.sh**

That's what I thought I was doing that didn't work, but this:

```
**sudo cp ~/Documents/Scripts/reconnect.sh /usr/local/bin/reconnect**

**d ALL=NOPASSWD: /usr/local/bin/reconnect**
```

was perfect. Thanks.

---

