---
title: "How do I tell which version, 32 or 64?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Vinegarcat on 2008-08-14
How do I tell which version I have, because I don't honestly remember which I got.  32 or 64?  My system is 64 so it's somewhat important.

---

### Post by Vivaldi Gloria on 2008-08-14
In a terminal give the command 

```
uname -a
```

If you get

```
i686 GNU/Linux
```

at the end then it's 32 bit.

If you get 

```
x86_64  GNU/Linux
```

at the end then it's 64 bit.

---

### Post by iaculallad on 2008-08-14
The best way would be to input the command below on your terminal:

```
uname -m
```

x686 = 32-bit
x86_64 = 64-bit

---

### Post by Vinegarcat on 2008-08-14
64 bit thanks :)

---

