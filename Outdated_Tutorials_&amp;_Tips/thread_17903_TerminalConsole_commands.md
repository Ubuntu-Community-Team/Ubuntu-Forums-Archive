---
title: "Terminal/Console commands"
date: 2005-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Mark Marple on 2005-03-03
Hello to all,
   I'm new to Ubuntu and loving it more and more everyday.  Probably the best Linux distro that I have used (and I have tried alot....... :D )  Anyhow, just wanted to give PROPS to this distro.

My question is that I'm trying to create a Launcher on the desktop to start a terminal/console and then run the "df --human-readable" command to list my harddrive info.

currently in the command area I have "gnome-terminal df --human-readable".  This does nothing, as I know I'm messing up.  I was wondering if someone can help me out and tell me what needs to go in between the "terminal" and "df" text to open the terminal and run the command.  Can this even be done?

the df command works if I start a terminal the normal way from the applications menu. 

Thanks in advance for any help!

---

### Post by p!=f on 2005-03-03
[QUOTE=Mark Marple]Hello to all,
   I'm new to Ubuntu and loving it more and more everyday.  Probably the best Linux distro that I have used (and I have tried alot....... :D )  Anyhow, just wanted to give PROPS to this distro.

My question is that I'm trying to create a Launcher on the desktop to start a terminal/console and then run the "df --human-readable" command to list my harddrive info.

currently in the command area I have "gnome-terminal df --human-readable".  This does nothing, as I know I'm messing up.  I was wondering if someone can help me out and tell me what needs to go in between the "terminal" and "df" text to open the terminal and run the command.  Can this even be done?

the df command works if I start a terminal the normal way from the applications menu. 

Thanks in advance for any help![/QUOTE]

First you need to edit the settings in gnome-terminal. Run it -> right click -> edit current profile -> second tab (sorry I don't have it in English here :)) -> command -> and select "let terminal opened" after the command executes

Next, right click on a gnome-panel you want to add your launcher -> add your own launcher -> type df -h for command and click on "run in terminal".

BTW, There's nice GTK apps called gtkdiskfree you might be interested in. ;)

---

### Post by bored2k on 2005-03-03
[QUOTE=p!=f]First you need to edit the settings in gnome-terminal. Run it -> right click -> edit current profile -> second tab (sorry I don't have it in English here :)) -> command -> and select "let terminal opened" after the command executes

Next, right click on a gnome-panel you want to add your launcher -> add your own launcher -> type df -h for command and click on "run in terminal".

BTW, There's nice GTK apps called gtkdiskfree you might be interested in. ;)[/QUOTE]

He meant:

Edit > Current Profile > Title and Command > When command exists: Hold the terminal open.  =D>

---

### Post by Mark Marple on 2005-03-03
thank you p!=f and bored2k

I tried the console items that you mentioned, but it only opened the terminal window without any commands.  Thats ok though, as I installed the GTKdiskfree and set it up on the gnome-panel as a launcher.  This is perfect!  Thank you for pointing me in the right direction.

---

### Post by p!=f on 2005-03-03
[QUOTE=bored2k]He meant:

Edit > Current Profile > Title and Command > When command exists: Hold the terminal open.  =D>[/QUOTE]
Thanks for the corrections. :)

---

