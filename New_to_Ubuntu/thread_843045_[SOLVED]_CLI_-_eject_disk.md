---
title: "[SOLVED] CLI - eject disk"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-27
how do I open my dvd drive from the terminal?  is this possible?

---

### Post by wolfen69 on 2008-06-27
```
eject /cdrom

```

---

### Post by RomeReactor on 2008-06-27
Hi. Yes you can; you just need to know its designation in the **/dev** directory. My dvd drive is **/dev/dvd2**, so i open it like this:
```
eject /dev/dvd2
```
And to close the tray:
```
eject -t /dev/dvd2
```

---

### Post by adamogardner on 2008-06-27
excellent! thankyou

---

