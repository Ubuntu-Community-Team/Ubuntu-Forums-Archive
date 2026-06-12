---
title: "How to identify which Xubuntu version is on a PC?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by candtalan on 2012-05-16
I am helping someone who has Xubuntu but I do not know which version
how to identify which Xubuntu version please?
tia

---

### Post by december0123 on 2012-05-16
Hi! Type this into your terminal: 
 ```
cat /etc/issue
```

You can also try this: 
```
lsb_release -a
```

---

### Post by candtalan on 2012-05-16
Thanks!

---

### Post by codemaniac on 2012-05-16
To add more to december0123's suggestion
you can go into System Settings and open System Information .A non commandline way.

---

### Post by mörgæs on 2012-05-16
Good. If this solves your problem, please mark the thread so.

---

### Post by candtalan on 2012-05-16
> **december0123 said:**
> Hi! Type this into your terminal: 
 ```
cat /etc/issue
```

You can also try this: 
```
lsb_release -a
```

Thnaks these both work in Ubuntu 11.10

---

### Post by candtalan on 2012-05-16
> **codemaniac said:**
> To add more to december0123's suggestion
you can go into System Settings and open System Information .A non commandline way.
Thanks for the comment. Yes, I was initially looking for a non cl method, but could not then find one. The laptop (a friend's) had been installed with a little customisation (by a young geek relative), and I thought the gui methods were giving a problem because of that. But I am just now using a xubuntu live cd, and I still cannot find system settings(whatever), I conclude that such as that is not included in 11.10 (?) I did, though, eventually recall that Update Manager > other software or similar, probably listed the original CD (!) and that did help confirm 11.10  :-)

---

