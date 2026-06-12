---
title: "Wireless Installation Problem"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Lecter on 2008-06-09
I'm trying to instal Intel Wifi driver for a wireless network card (the 3945), I found a linux driver for it via the web,  and tried to install it.

The problem is about permissions... I open a terminal and follow instruction, I'm unable to use the "cp" command in the file "lib" because I dont have permission, this is quite troublesome...

---

### Post by powerpleb on 2008-06-09
> **Lecter said:**
> I'm trying to instal Intel Wifi driver for a wireless network card (the 3945), I found a linux driver for it via the web,  and tried to install it.

The problem is about permissions... I open a terminal and follow instruction, I'm unable to use the "cp" command in the file "lib" because I dont have permission, this is quite troublesome...

use sudo... eg.
```
sudo cp /path/file /destination/
```
This gives you root (administrator) privileges whenever you run a command.

---

### Post by arckeda on 2008-06-09
You should use sudo before your commands, however, if you don't want to have to keep typing sudo, you can type:

sudo -s

To maintain root abilities, or open a root shell with:

sudo sh

You should also change your root account password if you have not already, to do this type:

sudo sh

passwd


And remember, you won't be able to see yourself type your password.


     -ARCKEDA

---

### Post by Lecter on 2008-06-09
Thanks that should do it.

---

