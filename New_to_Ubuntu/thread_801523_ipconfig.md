---
title: "ipconfig?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-20
What's the terminal command eqivelent for the M$ CLI command "ipconfig  /all"?

thanks.........

---

### Post by mapes12 on 2008-05-20
```
ifconfig
```

and also type

```
man ifconfig
```

in a terminal window for all switches.

---

### Post by dwhitney67 on 2008-05-20
```
ifconfig -a
```

or alternatively

```
ifconfig
```

If you want to list info about a specific device:

```
ifconfig <device>
```

For example:

```
ifconfig eth0
```

---

### Post by chadwit on 2008-05-20
excellent...gracias amigo!!!

---

