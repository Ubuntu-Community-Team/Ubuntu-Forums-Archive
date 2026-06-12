---
title: "Ethernet not working"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-09-08
I tried connecting my Ethernet cable and I can't connect to the Internet. Is there any configuration I can make to fix this. My wireless works perfectly but in place where I can't access any wireless connection, I try to use my Ethernet cable and it doesn't connect. Any help??? Thanks in advance.

---

### Post by handydan918 on 2008-09-10
> **G!zZm0 said:**
> I tried connecting my Ethernet cable and I can't connect to the Internet. Is there any configuration I can make to fix this. My wireless works perfectly but in place where I can't access any wireless connection, I try to use my Ethernet cable and it doesn't connect. Any help??? Thanks in advance.

A litle short on detail,  but try opening a terminal and doing ```
sudo dhclient
```

That may get you up and running.

---

### Post by iaculallad on 2008-09-10
Or to complete the command above:

```
sudo dhclient -r
sudo dhclient
sudo /etc/init.d/networking restart
```

---

### Post by halitech on 2008-09-10
if it has never worked before, could you open a terminal and post the output of```
lspci
``` so we can see what kind of hardware you have

---

### Post by Gonz_91 on 2008-09-10
> sudo /etc/init.d/networking restart

All this command does is restart the networking, right?

---

### Post by iaculallad on 2008-09-10
> **Gonz_91 said:**
> All this command does is restart the networking, right?

You got it right.

---

### Post by Gonz_91 on 2008-09-10
> **iaculallad said:**
> You got it right.
Thanks ^^,

---

