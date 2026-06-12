---
title: "network query"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-07-14
Hi,

When I open system monitor, I can see that some data is being sent from my computer.( although sent/received is quite low) I would like to what's going on.:)

---

### Post by kdcoetzee on 2008-07-14
the best way to see what is going on is tcpdump.

```
sudo tcpdump -i eth0
```

and the other program is iftop, but you need to install it first.

```
sudo apt-get install iftop
```

then you can run it with 

```
sudo iftop -i eth0
```

---

