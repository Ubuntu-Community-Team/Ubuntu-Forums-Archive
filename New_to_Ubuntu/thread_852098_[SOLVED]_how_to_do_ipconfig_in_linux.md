---
title: "[SOLVED] how to do ipconfig in linux?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by appoloin on 2008-07-07
whats the command to do ipconfig in linux? sorry for a dumb question

---

### Post by linuxisfree on 2008-07-07
> **appoloin said:**
> whats the command to do ipconfig in linux? sorry for a dumb question

```
ifconfig
```

---

### Post by Siege1386 on 2008-07-07
run ifconfig in the terminal

---

### Post by cherva on 2008-07-07
```
ifconfig
``` You have to be root, so put a sudo infront of it or use a root terminal ( sudo su )

---

### Post by hyper_ch on 2008-07-07
no, you can just run ifconfig and/or iwconfig

---

### Post by linuxisfree on 2008-07-07
> **cherva said:**
> ```
ifconfig
``` You have to be root, so put a sudo infront of it or use a root terminal ( sudo su )

Actually i don't think so... i can ifconfig without using sudo and it still shows everything...

---

### Post by cherva on 2008-07-07
> **linuxisfree said:**
> Actually i don't think so... i can ifconfig without using sudo and it still shows everything...
Yes, but you can't edit the interfaces. And I suppose that is what appoloin whant to do because he is a windows user and he is used to edit configurations without a password

---

