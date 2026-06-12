---
title: "[SOLVED] root or super user konsole?????"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-08
where is the super user konsole,su doesnt work,ineed to find out how i can run a terminal as root,how can this be done?????
rick:confused:

---

### Post by mali2297 on 2008-08-08
Usually, you just put **sudo** in front of every command that needs root privileges. If you want to use it as su, make it **sudo -i** and you will have a root shell.

If you want to make a desktop shortcut to a root terminal, then you can use the command
```

kdesu konsole

```

---

### Post by tuxxy on 2008-08-08
[http://ubuntuforums.org/showthread.php?t=314097](http://ubuntuforums.org/showthread.php?t=314097)

---

### Post by kdorf on 2008-08-08
I usually run "sudo su -".

FYI, quantumstitch, Ubuntu devs don't advocate enabling the root account.

---

### Post by dje on 2008-08-08
> **kdorf said:**
> I usually run "sudo su -".

FYI, quantumstitch, Ubuntu devs don't advocate enabling the root account.

yes that is against the ubuntu security model, please read more [here]("http://ubuntuforums.org/showthread.php?t=765414"). you should prefer sudo to su. you can use this to get a root shell without enabling the root account:
```
sudo -i
```
or just use:
```
sudo *command*
```

dje

---

### Post by Oldsoldier2003 on 2008-08-08
> **kdorf said:**
> I usually run "sudo su -".

FYI, quantumstitch, Ubuntu devs don't advocate enabling the root account.

And it is against the forum policy as well. See this for more: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by SunnyRabbiera on 2008-08-08
Yeh running sudo is how we run su typically in Ubuntu and its variants, in some ways sudo is better as the root account is disabled and a lot of mistakes that newcomers make is by running the OS as root like in windows.

---

### Post by rixtr66 on 2008-08-08
sorry i posted this i didnt know.:(

---

