---
title: "Desktop Launcher v shell script"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by paulemony on 2013-01-29
Just curious but if create a shell script to launch an application  it presents a menu with **Run in terminal, Display, Cancel,**or **Run** options, but if I then use a Desktop Launcher pointed at the shell script instead the menu doesn't appear, the application runs immediately without the terminal. If I needed the terminal is there a way of seeing the menu using the launcher rather than the shell script itself?

---

### Post by Impavidus on 2013-01-30
Maybe you can have the launcher not point at the shell script itself but at a terminal with the shell script as argument:```
terminal -e script
```(Substitute the terminal you use. The -e argument seems pretty universal.)
This should run the script in a terminal.

---

### Post by omeomi on 2013-01-30
In the .desktop file that launches the application you can just add Terminal=true to make it start in a terminal.

To edit run this (replace MYAPP with the name of the application):
```
sudo gedit /usr/share/applications/MYAPP.desktop
```

---

### Post by paulemony on 2013-01-30
Not quite there, probably because I'm not grasping the details, I'm not sure what > Substitute the terminal you use means exactly, if I just use **terminal -e** in front of the existing command in the desktop launcher I just get > Failed to execute child process "terminal" (No such file or directory).
I assume > the .desktop file that launches the application refers to the Python script that came with the application (obviously the target of the desktop launcher) which ultimately launches the app but that offers the terminal option anyway without > Terminal=true being added, & if I do add it it makes no difference to the desktop launcher which still opens app without terminal. What am I missing?

---

### Post by Impavidus on 2013-01-30
For the first one (the one I came up with), I meant with "substitute the terminal" use the command that launches your favorite terminal, like gnome-terminal, xfce4-terminal or xterm. So that gives you```
gnome-terminal -e "script -with -arguments"
```The suggestion by omeomi sounds somewhat better to me. The .desktop file is the desktop launcher, not the python script that launches the application (you didn't even tell your script was used to launch an application).

---

### Post by paulemony on 2013-01-30
Actually **gnome-terminal -e** stuck in front of the existing command in Desktop Launcher (pointed directly at the python script, the shell script was just an experiment) seems to have done it. Never seen **gnome-terminal** before, just use **Applications/Accessories/Terminal** hence confusion!

---

