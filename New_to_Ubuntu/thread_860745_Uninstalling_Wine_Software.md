---
title: "Uninstalling Wine Software"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Checkhovian on 2008-07-15
Hello,

Running Ubuntu (Hardy) with Wine 0.9.59, and want to know how I can get things I installed with Wine OFF of my computer. "Uninstall Wine Software" says it's uninstalled, but it's all still there....

---

### Post by iaculallad on 2008-07-15
> **Checkhovian said:**
> Hello,

Running Ubuntu (Hardy) with Wine 0.9.59, and want to know how I can get things I installed with Wine OFF of my computer. "Uninstall Wine Software" says it's uninstalled, but it's all still there....

Try:

```
sudo dpkg -r wine
```

and remove the .wine folder located in your home directory:

---

### Post by UbuntuNerd on 2008-07-15
Basically you need to remove these files manually. First go to your hidden files in your home directory.

Places>/home/<your user name>/.local/share/applications/wine/Programs

---

### Post by webofunni on 2008-07-15
Hi,

```
dpkg -l | grep -i wine
```

Will give all the applications related to wine eg : wine-doors etc .. 

You can use : 

```
 apt-get remove wine
apt-get purge wine
```

to remove them, Also remove the files inside your home folder manually

---

