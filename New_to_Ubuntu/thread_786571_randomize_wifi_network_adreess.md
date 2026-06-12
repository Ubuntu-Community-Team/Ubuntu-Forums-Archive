---
title: "randomize wifi network adreess"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-08
just happened to come across this
pretty usefull i think...
and how to do this?

---

### Post by Monicker on 2008-05-08
What do you mean? Are you talking about the SSID? The mac address?

---

### Post by lunaluna on 2008-05-08
> **Monicker said:**
> What do you mean? Are you talking about the SSID? The mac address?

yeap

---

### Post by Monicker on 2008-05-08
Yes to which question?  Changing either the mac address or the ssid is trivial to do.

---

### Post by lunaluna on 2008-05-08
mac....

---

### Post by Monicker on 2008-05-08
> **lunaluna said:**
> mac....

Install the macchanger application, or manually modify /etc/network/interfaces and add the following for the interface:

```
hwaddress ether <mac address>
```

---

### Post by lunaluna on 2008-05-08
> **Monicker said:**
> Install the macchanger application, or manually modify /etc/network/interfaces and add the following for the interface:

```
hwaddress ether <mac address>
```

which what exacly does?  (newwwwbbbeeeee)

---

