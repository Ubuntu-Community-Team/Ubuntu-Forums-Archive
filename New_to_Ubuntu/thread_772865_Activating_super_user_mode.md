---
title: "Activating super user mode"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ohav on 2008-04-28
how can I activate the super user mode in Ubuntu (the latest version) ?

---

### Post by LaRoza on 2008-04-28
> **ohav said:**
> how can I activate the super user mode in Ubuntu (the latest version) ?

```

sudo -i

```

If you want to log on as root, see the sticky in the Security forum.

---

### Post by Oldsoldier2003 on 2008-04-28
> **ohav said:**
> how can I activate the super user mode in Ubuntu (the latest version) ?

```
sudo somecommand
```
 or for a shell

```
sudo -i
```

---

### Post by keylime on 2008-04-28
Have you tried at the command line the sudo command?

---

### Post by alienexplorers on 2008-04-28
sudo for non-graphical programs or if running a graphical program use gksudo.

---

### Post by naklinaam on 2009-11-08
Adding a variant to the above question.
I can open a new thread if required

I am logged in as a non sudoer user. However, I want to be able to access some specific sudo commands. Ubuntu 9.10 prompts for the user and password when I try to install apps using the gui. I want a similar option where I can run commnads from the command line by specifying a super user user and passwrod without having to log into the superuser account first.
Any way this can be achieved?

---

### Post by ace007 on 2009-11-08
You can tell the `sudo' function which user you want it to run as.

This is done by ```
sudo -u USERNAME COMMAND
```

I found this out by typing ```
man sudo
```. You can find out all about commands by using the `man' function.

---

