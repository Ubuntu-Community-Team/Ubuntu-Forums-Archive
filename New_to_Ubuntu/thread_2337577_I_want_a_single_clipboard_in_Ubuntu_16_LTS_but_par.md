---
title: "I want a single clipboard in Ubuntu 16 LTS but parcellite doesn't work"
date: 2016-09-19
forum: New to Ubuntu
---

### Post by newnotice on 2016-09-19
I'm trying to make Ubuntu's clipboard more like Windows so that when I select something in the terminal it is in the same clipboard as if I selected something and right-click copied it. In other words I want a single clipboard. I found some answers by googling but they are all many years old and do not seem to work with Unity. I did read parcellite works with Unity according to its webpage so I installed it (apt-get install parcellite) but it doesn't do anything when I open it. The icon appears for a second and then disappears. I ran it from the terminal and it says this:

```
Looking in '/etc/xdg/xdg-ubuntu/parcellite/parcelliterc'
Looking in '/usr/share/upstart/xdg/parcellite/parcelliterc'
Looking in '/etc/xdg/parcellite/parcelliterc'
Looking in '/etc/xdg/xdg-ubuntu/parcellite/parcelliterc'
Looking in '/usr/share/upstart/xdg/parcellite/parcelliterc'
Looking in '/etc/xdg/parcellite/parcelliterc'
[text from the clipboard was on this line]
** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>P' failed!


** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>H' failed!


** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>X' failed!


** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>A' failed!

Flag 0x0001, status 256, EXIT 1 STAT 1
Looking in '/etc/xdg/xdg-ubuntu/parcellite/parcelliterc'
Looking in '/usr/share/upstart/xdg/parcellite/parcelliterc'
Looking in '/etc/xdg/parcellite/parcelliterc'
```
```
Package: parcellite
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 683
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.1.9-1
```

---

### Post by CantankRus on 2016-09-19
Try glipper.
```
sudo apt install glipper
```
Type glipper into the alt+F2 command shortcut to start.

In preferences you can choose which clipboards are managed by glipper.

---

### Post by newnotice on 2016-09-21
The problem is it's still a dual clipboard. I basically want the clipboard like it is in windows. If I'm in gedit or some other gui and I select something I don't want it going into the clipboard unless I choose cut or copy. However terminal I'm ok with if I select something it goes in automatically.

---

### Post by CantankRus on 2016-09-21
Don't have windows and don't know how it behaves.
Clipbord managers can monitor one of or both...
[LIST]
[*]primary selection ....left mouse highlight/middle mouse paste
[*]secondary selection....ctl+c/ctrl+v (in terminal you use ctrl+shift+c/ctrl+shift+v)
[/LIST]
If you choose to manage secondary selection only, the primary selection paste is still available via mouse middle click.
This is the way most prefer otherwise the clipboard history is filled too quick.
    
Don't know how or if you can make the clipboard behave differently in separate applications.

---

### Post by Bucky Ball on 2016-09-21
xfce4-clipman. It's universal and light. Lives in the taskbar and you can access it from anywhere. Should work fine with Ubuntu and will be in the repositories. Don't know what it needs to drag in from xfce4, but it would be minimal I'd imagine. Install

```
xfce4-clipman
```

... from a terminal or whatever package manager you use. If it doesn't also drag in the following, also install

```
xfce4-clipman-plugin
```

---

### Post by Habitual on 2016-09-21
clipit?

---

### Post by oldrocker99 on 2016-09-21
There's diodon, as well.

---

### Post by rickyrockrat on 2016-09-28
> **newnotice said:**
> I'm trying to make Ubuntu's clipboard more like Windows so that when I select something in the terminal it is in the same clipboard as if I selected something and right-click copied it. In other words I want a single clipboard. I found some answers by googling but they are all many years old and do not seem to work with Unity. I did read parcellite works with Unity according to its webpage so I installed it (apt-get install parcellite) but it doesn't do anything when I open it. The icon appears for a second and then disappears. I ran it from the terminal and it says this:

** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>P' failed!
** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>H' failed!
** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>X' failed!
** (parcellite:3151): WARNING **: Binding '<Ctrl><Alt>A' failed!



Usually this means something else is binding the hot keys for the pop up.Good job on running it from the terminal, btw. Go to your keyboard bindings and try to disable them. Without any key bindings, it's hard for Parcellite to be useful to you. Since I'm the developer, I've added a bug ticket here:

[https://sourceforge.net/p/parcellite/bugs/148/](https://sourceforge.net/p/parcellite/bugs/148/)

And here are ways to get to your keybindings:
[http://askubuntu.com/questions/37313/how-do-i-deactivate-f1-and-f10-keybindings-in-gnome-terminal](http://askubuntu.com/questions/37313/how-do-i-deactivate-f1-and-f10-keybindings-in-gnome-terminal)

---

