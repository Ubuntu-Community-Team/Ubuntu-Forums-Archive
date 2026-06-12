---
title: "Can't edit my menu in Ubuntu 13.04"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by angelsimon on 2013-11-08
Hi everyone, I've installed gnome-panel because I prefer the old desktop rather than Unity. Everything works ok but I can't edit the Classic menu. I mean, if I open the application to edit the principal menu it simply doesn't let me add new menues nor submenues.
It doesn't either let me drag and drop items from a menu to another.

Is there something I can do to customize my Main menu as I wish?

Thanks in advance!

---

### Post by ibjsb4 on 2013-11-09
Are you saying '[alacarte]("https://apps.ubuntu.com/cat/applications/raring/alacarte/")' will not work?  If so, try [opening it in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and look for errors.

```
alacarte
```

---

### Post by Frogs Hair on 2013-11-09
I haven't tried to create sub-menus in the gnome-panel sessions using alacarte and will let you you know if I have the same problem. Alacarte is a carry over from Gnome 2 and I don't know if it functions the same way in Gnome 3.

Edit: I am also unable to create sub-menus with the main menu , but can create launchers and customize icons.

---

### Post by angelsimon on 2013-11-10
Yes, i didn't know it ¡s named 'alacarte'. When I open it in terminal shows the following output:

> (alacarte:2842): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:2842): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed



Thanks

---

### Post by ibjsb4 on 2013-11-11
Gtk-CRITICAL; I get those too.  Don't think thats the problem.  You say that you click on applications in the main box, but cannot create a sub-menu.  Should be able to do that.  Try recreating your main-menu configuration file in terminal.

> mv ~/.config/menus ~/.config/menus.old

If that does nothing, try reinstalling one or two packages.
> 
sudo apt-get remove --purge alacarte && sudo apt-get install alacarte

You can also try reinstalling your main-menu, which is called **gnome-menus** in terminal.  Just replace alacarte with gnome-menus in the above command.

Any customization you have done to the menu will be removed by doing this.

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

