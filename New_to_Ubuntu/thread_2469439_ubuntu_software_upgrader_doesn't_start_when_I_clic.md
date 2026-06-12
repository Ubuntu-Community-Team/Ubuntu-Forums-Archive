---
title: "ubuntu software upgrader doesn't start when I click on the icon"
date: 2021-11-29
forum: New to Ubuntu
---

### Post by eliyahu22 on 2021-11-29
I'm using Ubuntu  20.04 LTS, and when I click on the icon for the software updater, he doesn't start.  Is there a command for the terminal to start is?

---

### Post by ActionParsnip on 2021-11-29
Try
```

sudo software-center

```
Or
```

sudo gnome-software-center

```

---

### Post by KBar on 2021-11-29
Do you mean the *Software Updater* app? You can start it from the shell with this command:
```
update-manager
```

Analogously, you can also invoke *apt* like so
```
apt update
```
which will first fetch the sources and tell you if there are packages that can be upgraded.
```
apt list --upgradable
```
will list those packages. If you're ready, run
```
apt upgrade
```
to upgrade them.

*apt* requires superuser privileges.

---

### Post by ajgreeny on 2021-11-29
Don't forget that you will have to run all the **apt** commands shown by **kbar** as root, and will therefore have to use **sudo** before each command, ie, ***sudo apt update*** etc etc.

---

### Post by KBar on 2021-11-29
> **ajgreeny said:**
> Don't forget that you will have to run all the **apt** commands shown by **kbar** as root, and will therefore have to use **sudo** before each command, ie, ***sudo apt update*** etc etc.

No. By default, credentials are cached for 15 minutes per terminal. Running it once (in the beginning) is sufficient.

---

### Post by ajgreeny on 2021-11-30
But you still need to use **sudo** except for the **apt list**, though you will not need to enter your password again as that is what will be cached.

---

### Post by KBar on 2021-11-30
That's what I've said, yes.

---

### Post by ActionParsnip on 2021-11-30
If you run
```

sudo apt update
sudo apt full-upgrade

```
Does it work OK?

---

### Post by eliyahu22 on 2021-12-01
> **ActionParsnip said:**
> If you run
```

sudo apt update
sudo apt full-upgrade

```
Does it work OK?

When I tried this command: update-manager I got the update manager.  

It is just that I made a mistake, it is not the software update manager I have problems with, it is the Ubuntu Software icon that doesn't work.   That is the square orange icon, which let's you install all kind of programs for Ubuntu.   That one doesn't do anything.

---

### Post by Frogs Hair on 2021-12-01
Try the following command and report any errors.

```
gnome-software
```

---

