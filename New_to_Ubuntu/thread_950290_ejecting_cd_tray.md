---
title: "ejecting cd tray"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by bull205 on 2008-10-17
Anyone know how to eject a laptop cd tray?  The hard button on the actual tray doesn't eject the tray when booted in ubuntu.  I have to insert a paper clip to get it open...not real convenient.

---

### Post by Keen101 on 2008-10-17
try typing eject in the terminal.

```
eject
```

---

### Post by bull205 on 2008-10-17
ain't that peachy!!! Awesome.  Can I make some sort of icon on my desktop and make it run that command so I can double click the icon and have the drive pop open?

---

### Post by Keen101 on 2008-10-17
```
bash -c "eject"
```

I just learned how to do that the other day. :D

not for ejecting, but how to make a shortcut to my ardunio software. It seems it can be applied to anything.

---

### Post by nothingspecial on 2008-10-17
I use a keyboard shortcut.

In your preferences menu.

I use Ctrl/Shift+E

---

### Post by bull205 on 2008-10-17
> **Keen101 said:**
> ```
bash -c "eject"
```

I just learned how to do that the other day. :D

not for ejecting, but how to make a shortcut to my ardunio software. It seems it can be applied to anything.

How do you "apply" that to an icon?

---

### Post by panhandle on 2008-10-17
Making the icon is easy. Use the launcher.

Right click on your desktop-->Create Launcher

1) Give the icon a name like "CD eject"

2) In "command" dialog box enter > eject

3) Comment on functionality, if you want.

Click OK, et voila.

---

### Post by bull205 on 2008-10-17
that's easy enough, but what is the bash -c eject command that Keen101 was talking about?  How is that used?

---

### Post by Keen101 on 2008-10-17
panhandle solution is basically correct.

1. Right click on desktop

2. select "create launcher" option

3. give icon a name, and in the "command" area put in you terminal commands.

**in this instance plain old "eject" seems to work, but sometimes for more advanced commands or a string of commands... that doesn't work, and you need the bash -c "" options.**

also, nothingspecial mentioned that you can create a keyboard shortcut. >System >Prefrences >keyboard shortcuts.

---

### Post by bull205 on 2008-10-17
SUPERNOOB alert!!! What does the bash command do?

---

### Post by Keen101 on 2008-10-17
**the terminal is called the bash shell**. so the command i gave you practically say's that the following command should be run in the bash shell.

you can google to find out more. anyway, i hope you solved your problem. good luck, and keep on learning.

i guess there are other types of linux shells, but the bash shell is the most common.

edit:  oh yeah, i forgot about that. just do what kansasnoob recomends. I use it all the time, and i forgot about it only now. heh the irony. just right click on your cd icon on the desktop.

---

### Post by panhandle on 2008-10-17
open a terminal and type 

> man bash

:)

---

### Post by kansasnoob on 2008-10-17
You should not have to use the command line at all to do that.

You should be able to use *window switcher* or *show desktop* from the panel and see the "drive" on the desktop like this:

[ATTACH]88589[/ATTACH]

Then just choose to eject:

[ATTACH]88590[/ATTACH]

It's user friendly!

---

