---
title: "where are my programs?"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2014-01-17
I have just installed Ubuntu 12 LTS and don't know how to run any of the installed programs. Also, is it possible to create desktop icons.

---

### Post by sandyd on 2014-01-17
Welcome to Ubuntu!
On the left side of the screen, click on the Ubuntu Dash (the button with the Ubuntu Logo), and type in any application you want to run :)

---

### Post by ian-weisser on 2014-01-17
> **George_McEwan said:**
> I have just installed Ubuntu 12 LTS and don't know how to run any of the installed programs.
Well, that seems patently untrue. 
You obviously figured out how to run the web browser.


 > **George_McEwan said:**
> Also, is it possible to create desktop icons.
Yes...but Unity is designed so you don't need to.
Trying to recreate your old experience in a new environment will be endlessly frustrating. Been there. Try it the Unity way first.

---

### Post by HappyAsHellas on 2014-01-17
Do I have to do this every time I want to run a program? How can I create a desktop icon for ease of use?

---

### Post by HappyAsHellas on 2014-01-17
What is Unity and how do I use it. Sprry for missing a post

---

### Post by Christmas on 2014-01-17
You can press the Super key (Windows Logo key) to open Dash, then type the name of programs there (like terminal, of firefox etc). You can also press Alt+F2 and type the full name of the program there (e.g. gnome-terminal) and press Enter. You can also add shortcuts to programs in the left launcher panel and you can also create desktop icons (I believe by right-clicking on the desktop - I'm in KDE right now). Or you can open Gedit and manually create desktop files like this:
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Firefox
GenericName=Web Browser
Type=Application
Exec=firefox
Icon=firefox.png

```
This will create a Firefox launcher.

You can find all your installed applications in /bin and /usr/bin (launch the file browser to navigate to them).

---

### Post by deadflowr on 2014-01-17
You could try a drag and drop from the dash menu and place the app on the desktop.
But then it becomes redundant because whenever you launch the app an icon will appear on the dock/launcher on the left.

There are multiple ways the open the dash, the easiest is the mouse, and if you right click on the the dash icon, you will see a drop down of other options. Options that will let you open specific parts of the dash.

If you use the keyboard, then to open the dash, press the super key(that is the windows icon key on the keyboard).
Also, you can use several keybinding which are in place, such as super + A, which will open the dash applications menu.
Others include super + F for the files menu, and super + V for the videos menu.

Another thing is the help shortcut overlay, press and hold the super key and an overlay window will show and it has a list of the keyboard shortcuts and such.

That's just a few things for you,
Have fun.

---

### Post by kajoky on 2014-01-17
After starting a program, if you will be using it frequently, you can right click on the program's icon on the left side of the screen. A menu should appear. Click Lock to Launcher.  That program icon will stay in the launcher to make it easier to launch.

---

### Post by HappyAsHellas on 2014-01-17
Thanks for all the help

---

