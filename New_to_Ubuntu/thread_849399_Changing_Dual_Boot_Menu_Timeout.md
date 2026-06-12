---
title: "Changing Dual Boot Menu Timeout"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by harry01 on 2008-07-04
First time user of Hardy Heron. When I do all this (below) it asks me for the password but won't let me type it in. If this method is outdated then how do I change it? How do I type in the password to proceed to the Text Editor?

Press Applications &#8594; Accessories &#8594; Terminal.

The Terminal screen will appear. Type the following into the Terminal, entering your administrative password if prompted:

cd /boot/grub
sudo cp menu.lst menu_backup.lst
sudo gedit menu.lst
                            Thanks....Harry

---

### Post by Elfy on 2008-07-04
just type it in - you won't see it. it's invisible

You don't have to do all the cd /boot /grub you could add the path into the commands

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst

If you are going to be using a gui app use gksudo instead of sudo

---

### Post by jombeewoof on 2008-07-04
just type the password and hit enter, it will register. 
the cli doesn't show you anything when you're typing in the password.

You want to follow the instructions you have, they will work.

The parameter you want to change is titled timeout or something like that, change it to a value in seconds that you want.

---

### Post by sayakb on 2008-07-04
You may use Startup manager for adjusting GRUB settings:
```
sudo apt-get install startupmanager
```

Start it from System->Administration->Startup-manager

---

### Post by bumanie on 2008-07-04
Typing in your password in terminal does not produce any visual output. Also to back up /boot/grub/menu.lst it is > sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup To change time out > sudo gedit sudo boot/grub/menu.lst  will allow you to edit the time out with gnome editor.

---

### Post by Elfy on 2008-07-04
> **LinuxIsInnovation said:**
> You may use Startup manager for adjusting GRUB settings:
```
sudo apt-get install startupmanager
```

Start it from System->Administration->Startup-manager

You could use it but I think it's a lot easier to do it manually without installing extras, also you get used to the terminal which is quite often the quickest way to achieve things.

Of course it's linux so mostly about choice :)

---

### Post by sayakb on 2008-07-04
> **forestpixie said:**
> You could use it but I think it's a lot easier to do it manually without installing extras, also you get used to the terminal which is quite often the quickest way to achieve things.

Of course it's linux so mostly about choice :)

Right you are! There are GUI alternatives for almost everything now.. But nothing can beat the CLI ;)

---

### Post by harry01 on 2008-07-04
Problem solved. It was the password being invisible when typing it in. Thank you everybody for your help.......Harry

---

