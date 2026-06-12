---
title: "[SOLVED] Real Player will not install in 8.04"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by suomalainen on 2008-06-27
Hello,

I went to the real player website and downloaded "RealPlayer11GOLD.bin" onto my desktop. I then went to propeerties to make file executable. Thhen I double clicked file and get error message:

What can I do? Error message is attached. Thanks!!!

---

### Post by bumanie on 2008-06-27
Follow [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin")

---

### Post by wolfen69 on 2008-06-27
read [this]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin")

---

### Post by suomalainen on 2008-06-27
woops....! So far no luck.

How do you do this? "Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands: "

The file bin file is on my desktop.

---

### Post by suomalainen on 2008-06-27
What can I do?

---

### Post by dizee on 2008-06-27
> **suomalainen said:**
> woops....! So far no luck.

How do you do this? "Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands: "

The file bin file is on my desktop.
right i'll try walking you through it.

open the terminal (sort of like a command prompt window) by clicking on applications > accesories > terminal.

you will see a prompt like this:
```
user@computer:~$
```

you start off in your home folder (known as ~) so to change to your desktop folder, you use the "cd" (change directory) command.

```
cd Desktop
```

make the real player file executable (so it can run like a program) with the "chmod" (change permissions) command.

```
chmod 770 RealPlayer11GOLD.bin
```

(to save time typing you can use the tab button to autocomplete - type the first letters "Rea" and press tab.)

then you run the setup:

```
sudo ./RealPlayer11Gold.bin
```

("sudo" runs programs as administrator. the "./" tells the computer to run the program.)

you can safely use the default options in the setup.

real player should now be installed, but if you need the firefox plugin of it just use these commands:
```
cd /usr/lib/firefox-addons/plugins
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.
```

("ln -s" creates a symbolic link, basically a kind of invisible shortcut to where the program is. "mv" is the command to move or rename a file.)

you can simply copy and paste these commands as well.

---

### Post by Pjotr123 on 2008-06-27
You don't need Real Player to have 100 % multimedia support. Simply follow this easy how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

I don't like Real Player. In the bad old Windows days, it used to infect my computer like a virus.

---

### Post by dizee on 2008-06-27
> **Pjotr123 said:**
> You don't need Real Player to have 100 % multimedia support. Simply follow this easy how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

I don't like Real Player. In the bad old Windows days, it used to infect my computer like a virus.
i'm no fan of real player myself but i had no choice but to install it because the rte.ie website only supports it, and helix player didn't work. so there are cases where it's needed. generally though i would agree that people should avoid it (i used real player alternative on windows) since the program has a history of acting as spyware on windows.

---

### Post by suomalainen on 2008-06-27
Your the best dizee!!!! Thanks!

---

