---
title: "Running as root?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Anonono on 2008-10-01
I know this is a supernoob question, but... How?

---

### Post by Borusa on 2008-10-01
It is doable, by why, particularly, do you want to?

The way that Ubuntu is setup by default is for you to run as your user, but if you need to do something that requires superuser permissions, do "sudo <command>"

There are some apps (synaptic, for example) that do this "invisibly".

---

### Post by blakjesus on 2008-10-01
Well if you are talking about using the terminal then, type "sudo" (without the quotes) for applications you run in the terminal, and "gksudo" for GUI applications. :popcorn:

---

### Post by Paqman on 2008-10-01
Ubuntu isn't really set up to let you run as root.

If you need to run a terminal command with root privileges then just prefix it with "sudo". If you need to launch a graphical app as root, launch it with the prefix "gksudo" (you can launch an app through Alt-F2, btw)

---

### Post by aeiah on 2008-10-01
in grub you'll have a boot option that'll let you boot to root, but this is really only advisable if your normal user is broken and you need to fix it. the safe and standard way of doing things that require super user access is to use sudo

---

### Post by iaculallad on 2008-10-01
Or if you want to have the # prompt:

```
sudo -i
```

and after logging out (exit), make it expire:

```
sudo -k
```

---

