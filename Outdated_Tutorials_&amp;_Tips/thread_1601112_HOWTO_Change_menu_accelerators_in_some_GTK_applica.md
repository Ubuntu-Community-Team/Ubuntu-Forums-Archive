---
title: "HOWTO: Change menu accelerators in some GTK applications"
date: 2010-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by MaxIBoy on 2010-10-19
You know how sometimes, an application provides no way at all to change the keyboard shortcuts? Well, it turns out that for some GTK applications, at least one type of shortcut (the menu accelerator) can be changed fairly easily using a pretty simple trick. I'm going to explain it in a fairly simplistic tone so I don't loose any beginners, so if you're more of a power-user please bear with me. 

I should explain that a menu accelerator is a keyboard shortcut for a menu item. To explain in a diagram:
[[IMG]http://img156.imageshack.us/img156/2767/whatisanaccel.png[/IMG]]("http://img156.imageshack.us/i/whatisanaccel.png/")
This is the type of keyboard shortcut which can be changed using this method.

YOUR MILEAGE MAY VARY. I doubt very much that actual harm will come by trying this. However, it doesn't work on every program, only some of them. 

[LIST]
[*]First of all, it only works for GTK applications. [GTK]("http://en.wikipedia.org/wiki/GTK%2B") is essentially a toolkit used by computer programmers to make it easer to create graphical (point-and-click) software. There are a few other toolkits in common use besides GTK. If you use standard Ubuntu (with GNOME) or if you're using Xubuntu (with XFCE,) all of the default applications use GTK (although some of the software you installed later on may not.) This means that any software which doesn't seem to match your theme and appearance settings probably does not use GTK. If you use Kubuntu (with KDE,) that means all of your default applications use Qt instead, and you can only use this trick on any GTK applications you've installed yourself.
[*]Second of all, it doesn't even work on all GTK applications. It seems to be sort of hit-and-miss. For example, I know that it works with gedit, the standard GNOME text editor, but it doesn't work with gcalctool, the standard GNOME calculator utility. So if you can't get it to work on some program, try it first with gedit to make sure it's working at all.
[/LIST]




To start you should launch gconf-editor. This might be in your menus somewhere (with the name "configuration editor" or similar.) If you can't find it, you can launch it by hitting alt-f2 and typing in "gconf-editor" without the quotes, then hitting enter. In the side-pane, navigate to desktop>gnome>interface and click on it. Then check the box next to "can_change_accels." 
[[IMG]http://img143.imageshack.us/img143/373/canchangeaccels.png[/IMG]]("http://img143.imageshack.us/i/canchangeaccels.png/")

If you don't have an entry for "can_change_accels," create one by right-clicking and selecting "New Key," then filling out the form as follows. 
[[IMG]http://img267.imageshack.us/img267/2535/creatingkey.png[/IMG]]("http://img267.imageshack.us/i/creatingkey.png/")



Now, restart whatever program you are going to customize. Pull down the right menu and hover your mouse over whatever menu item you want to change. You can now change the accelerator just by typing a new one in. You can set accelerators for menu items that don't currently have them, and you can clear an accelerator from a menu item by hovering over it and hitting the delete key. Once again, you may discover that the program you're trying to customize doesn't support this option.

As soon as you are done changing the accelerators, I recommend that you go back to the gconf-editor window and uncheck the "can_change_accels" box to turn it back off. The changes you made should still be permanent, but by turning it off you won't change accelerators by accident. 



Congrats, you're done!

---

### Post by joonpy on 2010-10-22
Thank you very much for this. It is very helpful!

-Joon

---

