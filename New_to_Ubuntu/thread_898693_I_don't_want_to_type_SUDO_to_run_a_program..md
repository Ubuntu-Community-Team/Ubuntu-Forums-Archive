---
title: "I don't want to type SUDO to run a program."
date: 2008-08-23
forum: New to Ubuntu
---

### Post by dstin1 on 2008-08-23
I recently got my win modem to work which was a long process in itself.

Now in order to get on the internet I need to go to a terminal and type sudo martian_modem which creates /dev/ttySM0 then I need to go to another terminal and type sudo wvdial to dial out.

What I want to do is be able to use gnome ppp with out having to open a terminal to start martian modem.

So I need to know how to start martian modem at start up or how to create a icon that will start martian modem and then wvdial or gnome ppp.

I know it should be simple to change the permission of the program so I don't have to use sudo but I can't find the answer anywhere.

---

### Post by rossjman1 on 2008-08-23
You can make a script.
```

#!/bin/bash
cd /directory/where/martion_modem/is
sudo su
./martian_modem
wvdial

```

Then make the file executable
```

chmod ugo+x your_shell_script.sh

```
You can put this file on the desktop, or somewhere else, then make a launcher in the menu for this file. Should work. If not post errors here. You will still need to enter a password, but in a regular window (like when you run synaptics from the menu.

---

### Post by sdennie on 2008-08-23
You can likely just add your startup commands to the file /etc/rc.local.  That gets executed on startup and with root privileges.

---

