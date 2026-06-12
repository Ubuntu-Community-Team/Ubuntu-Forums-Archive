---
title: "[SOLVED] .bashrc question"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-18
I know that the .bashrc file in my home directory allows me to make aliases for gnome-terminal.  What I want to know is where do you go about making aliases for the root terminal?  I know it is a .bashrc file, but I don't know where it is.  Any help would be appreciated.

Donald Saunders

---

### Post by Joeb454 on 2008-06-18
I'm not 100% sure, but I would imagine it would be ```
/root/.bashrc
```

---

### Post by sisco311 on 2008-06-18
WARNING don't execute this command until you don't know exactly what are you doing.

You can use
```
sudo -s
```to start a root shell and keep the current shell's environment.(you can use the aliases from your $HOME/.bashrc file)

---

### Post by Joeb454 on 2008-06-18
You can indeed, but it's not recommended to do that :)

---

### Post by sisco311 on 2008-06-18
> **Joeb454 said:**
> You can indeed, but it's not recommended to do that :)
Yes. Starting a root shell is not recommended at all.

---

### Post by Joeb454 on 2008-06-18
No I meant running ```
sudo -s
``` Because it keeps your environment variables it ***can*** cause issues sometimes (root may get ownership of things in /home etc.) However unlikely it may be, it's something I don't want to happen.

You can run ```
sudo -i
``` if you wish to have a root terminal, because it then keeps root's own environment variables :)

---

