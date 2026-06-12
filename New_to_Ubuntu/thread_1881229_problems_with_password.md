---
title: "problems with password"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by kiedis on 2011-11-15
i don't understand password policy on ubuntu - for example, i have set the pw during the installation and use it to login to my pc and it works fine. But when i try to run command "shutdown -h 00:00" i get "it must be run as root", so i type in ''su'', press Enter, enter my username and password which i user at login to my pc and get authentication failure. What other password must i have in order to run this command?

---

### Post by nothingspecial on 2011-11-15
Hi, Ubuntu uses sudo.

Use ```
sudo shutdown -h 00:00
``` and authenticate it with your administration password (the one you log in with).

---

### Post by coffeecat on 2011-11-15
> **kiedis said:**
> i don't understand password policy on ubuntu

Hi. Have a look at this. Everything explained:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jroa on 2011-11-15
Ubuntu is not set up to use root to run commands as default.  You use sudo before the command instead.  Other distros, like Fedora, do allow you to switch to root to run commands using the su - command followed by the root password.

From what I understand, the root password in Ubuntu is a random unknown set of characters.  If you really want to run commands as root, which is not necessary, you can set the password by running the follow commands.

```

sudo su -
passwd

```

Then, set the root password.

---

### Post by overdrank on 2011-11-15
> **jroa said:**
> Ubuntu is not set up to use root to run commands as default.  You use sudo before the command instead.  Other distros, like Fedora, do allow you to switch to root to run commands using the su - command followed by the root password.

From what I understand, the root password in Ubuntu is a random unknown set of characters.  If you really want to run commands as root, which is not necessary, you can set the password by running the follow commands.

```

sudo su -
passwd

```

Then, set the root password.

Hi and _[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=1486138")_
```
sudo -i
``` :)

---

