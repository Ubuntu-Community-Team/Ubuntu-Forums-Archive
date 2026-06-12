---
title: "authentication failure at the command line"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-03
I'm having authentification failure when I "su," and type in the only password I know for this system.

---

### Post by ConMan318 on 2008-07-03
Use:
```

sudo su

```

or
```

sudo -i

```

---

### Post by Dr Small on 2008-07-03
The root account has no password by default, thus the authentication error. Try:
```
sudo su
```

---

### Post by adamogardner on 2008-07-03
success!  thankyou.

---

### Post by ChameleonDave on 2008-07-03
> **ConMan318 said:**
> Use:
```

sudo su

```

or
```

sudo -i

```

OK, but that assuming that he needs to totally become root.

He should probably just be putting "sudo" before the command he wants to run.

---

### Post by adamogardner on 2008-07-04
whats the "-i" argument?  it's not in my Linux In A Nutshell book.

---

### Post by ChameleonDave on 2008-07-04
> **adamogardner said:**
> whats the "-i" argument?  it's not in my Linux In A Nutshell book.

It is equivalent to "sudo su".

For further information, type "man sudo" at the command prompt.

---

