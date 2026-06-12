---
title: "How to block or remove menus in ubuntu?"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by thebazwaldo on 2008-09-26
Hello,

I have just installed Ubuntu for the first time. I have installed this to help a local charity. There will be children using theses machines for mostly internet and Open Office. I would like to block there access to as many things as possible. But really don't no where to start. I am aware I need to use terminal or root. But really could do with some useful command lines to disable things like option menus preferences that sort of this.

Many Thanks, Barry

---

### Post by forger on 2008-09-26
1) Applications > Add/remove > Search "All available applications" and search for **pessulus** (or **lockdown editor** )
It will help you lock most of gnome's utilities
2) System > Preferences > Main menu

---

### Post by Kinetic_lord on 2008-09-26
You can right click on a menu to remove it, and you can edit the menu contents by right-clicking>>edit menu's... put what they need over there and don't give them root privileges...

---

### Post by forger on 2008-09-26
and.. 3) it might be better to customize your ubuntu install, i.e. uninstall the applications that you don't need, through System > Administration > Synaptic package manager
Note that some applications might remove the ubuntu-desktop package, it's alright to remove it - that package would only be useful for various dependencies and for example, when you're upgrading to a newer release (i.e. from Hardy heron to the future Intrepid Ibex)

---

### Post by nothingspecial on 2008-09-26
[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)

That seems to cover the basics. As long as you don`t give them administrative capabilities and let them know the sudo password things will be ok - he says with hindsight.

---

