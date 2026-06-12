---
title: "gksu does not allow more than one parameter"
date: 2008-08-06
forum: Programming Talk
---

### Post by altonbr on 2008-08-06
I'm trying to run ```
gksu srm -r <folder>
``` but an error always returns because gksu does not recognize '-r'.

Why is gksu trying to read that far? Isn't it just for registering the root password like sudo? sudo has no problem with the command above, e.g.```
sudo srm -r <folder>
```

What can I do to register the password graphically?

---

### Post by nanotube on 2008-08-07
try using gksudo instead of gksu
(see man gksu and man gksudo for more info.)

---

### Post by jinksys on 2008-08-14
Simply put single quotes around the command.

```

$ gksu 'command -n'

```

not

```

$ gksu command -n

```

---

