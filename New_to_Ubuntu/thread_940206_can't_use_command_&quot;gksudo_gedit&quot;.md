---
title: "can't use command &quot;gksudo gedit&quot;"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-10-06
When ever i use the command
gksudo gedit /etc/modprobe.d/blacklist
I get the error message:
Gtk-WARNING **: cannot open display: 

Any ideas

---

### Post by matt1988 on 2008-10-06
Are you running this in a terminal in gnome?

try pressing Alt+F2 and putting gksudo gedit in there..if that doesn't work try just running gksudo..

let me know what happens.

---

### Post by drubin on 2008-10-06
are you running a Graphics environment? Or is this only a CLI?

---

### Post by matt1988 on 2008-10-06
Thats what I meant to ask when I asked if he was running it inside a terminal in gnome.

Also, just to make sure, you are not using ssh'ing into this computer and trying to run that are you?

---

### Post by drubin on 2008-10-06
> **matt1988 said:**
> Thats what I meant to ask when I asked if he was running it inside a terminal in gnome.

Also, just to make sure, you are not using ssh'ing into this computer and trying to run that are you?

If you are sshing (remote login) to the box you will not be able to run that command.

You will have to use something like 
```

sudo nano /etc/modprobe.d/blacklist
OR 

sudo vim /etc/modprobe.d/blacklist
```

I am not sure which editor you will be more comfortable with, or which one will be installed but try nano first if you are unsure.

---

### Post by KuroYoma on 2008-10-06
sorry to was your time i was using root in the terminal when i used the command
as soon as i was using the terminal as me it worked fine

---

### Post by matt1988 on 2008-10-06
I don't know why it would give you any problems while running gksudo as root, but there is no need to do so anyway. You already have su powers when you are root.

Anyway, glad everything is working for you. :)

---

