---
title: "upgrading from Gutsy to Hardy with Fluxbuntu"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by rockerphil on 2008-04-24
ok, here's the deal, i've been running Fluxbuntu 7.1 Gutsy Gibson on my old Dell Dimension desktop that's pretty well a dinosaur as far as machines go. here's my problem, i'm wanting to update from Gutsy to Hardy, but i have no CD burner and Fluxbuntu doesn't come with the Update Manager installed. so is there any way i can do this from the terminal? any help would be much appreciated

---

### Post by swoll1980 on 2008-04-24
If you have to computers you can use a network boot and do it that way
[http://tldp.org/HOWTO/Network-boot-HOWTO/index.html](http://tldp.org/HOWTO/Network-boot-HOWTO/index.html)

---

### Post by rockerphil on 2008-04-24
nope, only one computer. is there any way i can possibly run an upgrade from my command prompt?

---

### Post by swoll1980 on 2008-04-24
if you had an update manager you could. Is fluxbuntu the same as ubuntu, but with a different window manager? an upgrade  might not even be possable. If there not the same under the hood

---

### Post by rockerphil on 2008-04-24
yea, same OS under the hood, just using Fluxbox as my WM and ROX as my filer, just no upgrade manager (at least not that i can find)

---

### Post by hums07 on 2008-04-24
> **rockerphil said:**
> yea, same OS under the hood, just using Fluxbox as my WM and ROX as my filer, just no upgrade manager (at least not that i can find)

Just try this:
```
sudo apt-get install update-manager
```

You may need to edit your /etc/apt/sources.list. Check it.

---

### Post by andrewsomething on 2008-04-24
"sudo apt-get dist-upgrade" should do it, but update manager smooths over some of the rougher transitions durring upgrade. I'd go ahead and install it. If it pulls down too many un wanted dependencies, you can always uninstall after the upgrade.

---

