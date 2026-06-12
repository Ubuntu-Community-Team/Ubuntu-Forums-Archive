---
title: "Change xorg module"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by biji on 2008-09-01
hi all,
i'm new ubuntu user.. ubuntu is simple and just working ^^
how to change xorg module to intel? so that i have wide screen support because when i choose screen resolution there is no widescreen option

btw my chipset is intel gl965
thanks

---

### Post by fredwilby on 2008-09-20
try 

```

sudo gedit /etc/X11/xorg.conf

```

and change the "driver" entry in the "device" section to intel ( or make a driver entry if it doesn't exist )

be careful not to change anything else though, because a small mistake could stop x from working.

---

### Post by quinnten83 on 2008-09-20
> **fredwilby said:**
> try 

```

sudo gedit /etc/X11/xorg.conf

```

and change the "driver" entry in the "device" section to intel ( or make a driver entry if it doesn't exist )

be careful not to change anything else though, because a small mistake could stop x from working.

And for your deity of choice should you choose to have one's sake, make a backup of your xorg.conf so you can go back if everything goes belly up!

---

### Post by Shazaam on 2008-09-20
To be safe when graphically editing a file use
```
gksudo gedit
```
instead of just sudo.

---

