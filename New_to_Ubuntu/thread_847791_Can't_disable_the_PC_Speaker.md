---
title: "Can't disable the PC Speaker"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by TheSeb on 2008-07-02
I found many tutorials to disable the super annoying pc speaker. However, no matter how I input the command into the terminal, it always comes back with some sort of error and "Operation not permitted" 

help :(

---

### Post by iaculallad on 2008-07-02
On your terminal:

```
gksudo gedit /etc/modprobe.d/blacklist
```

Add this line to the end of the file:

```
blacklist pcspkr
```

And:

```
sudo rmmod pcspkr
```

to apply the changes without restarting.

---

### Post by TheSeb on 2008-07-02
thanks it worked :)

---

