---
title: "Starting Desktop Environment at startup"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by mariotre on 2011-11-07
I just installed Ubuntu Desktop 11.10 64-bit in a virtual machine.
Upon completion, I ended up at the command prompt.

I'm new to Ubuntu but I was expecting to bootup in a graphical environment (like gnome or kde).

What do I need to do to start a graphical environment?  

Regards,

Mario.

---

### Post by 3rdalbum on 2011-11-07
You should have booted to a graphical environment, as you suspect.

What virtual machine software are you using? Microsoft Virtual PC is not appropriate for any guest except Windows. Virtualbox is a good choice for using an Ubuntu guest.

Also, did you install Ubuntu and then fail to get a graphical login screen, or are you not getting a graphical display while the VM is booting from the CD?

---

### Post by haqking on 2011-11-07
> **mariotre said:**
> I just installed Ubuntu Desktop 11.10 64-bit in a virtual machine.
Upon completion, I ended up at the command prompt.

I'm new to Ubuntu but I was expecting to bootup in a graphical environment (like gnome or kde).

What do I need to do to start a graphical environment?  

Regards,

Mario.

are you sure you installed the server version and not the desktop version.

If you installed server there is no gui.

If you installed desktop then try:

```
sudo /etc/init.d/lightdm restart
```

or

```
sudo service lightdm start
```

---

### Post by mariotre on 2011-11-07
to 3rdalbum:
[INDENT]I'm using vmware workstation to manage my environment.  I did not see any errors during installation and I saw that the installation was proceeding in graphical mode.

[/INDENT]To haqking:
[INDENT]I did installed the Desktop, not server.
I will give a try to the commands you suggested and ping you back.

[/INDENT]Thank you both for your responses.

Mario.

---

