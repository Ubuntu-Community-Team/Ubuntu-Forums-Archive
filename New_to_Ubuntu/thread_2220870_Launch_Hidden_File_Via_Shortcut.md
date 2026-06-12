---
title: "Launch Hidden File Via Shortcut"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by insane9 on 2014-04-29
So I use 'SRWare Iron' browser. In order to run it, you have to use the terminal to CD into the iron64 folder and run the following command: ./iron

What I want to do, is create a shortcut on my desktop (or Unity bar) that will run the command and start iron. I tried creating a .desktop file but it wouldn't work. Can anyone help because I think this should be basic and i'm clearly overlooking something.

Many thanks.

---

### Post by pfeiffep on 2014-04-29
I may be off base here, but if you 'right click' on the desktop don't you get a prompt for new document? I use gnome flash back and that's the response when I right click.

Create a new document and make it a script to execute your command..

---

### Post by insane9 on 2014-04-29
I can create a blank document with: cd ~/Documents/iron64; ./iron 

But when I double click it, it just opens in gedit. I want it to be a launcher without using the terminal. I've made the file executable but it only executes from command line.

EDIT:

Ok I managed to do it. I did in fact need to create a .desktop file and make it executable (right click, properties, permissions and click the tick-box). 

Inside the launchBrowser.desktop file, I added the following:

[Desktop Entry]
Version=1.0
Type=Application
Hidden=false
Terminal=false
Icon=/home/YourUsernameGoesHere/Documents/iron64/product_logo_48.png
Name=ironLaunchpad
Exec=exec /home/YourUsernameGoesHere/Documents/iron64/iron
Path=/home/YourUserNameGoesHere/Documents/iron64/


And saved it and that's it. (This assumes your iron64 folder is in the Documents folder of your account)

---

### Post by pfeiffep on 2014-04-29
Glad to read that you perserved and solved your problem!

Please use the thread tools at the top to mark this solved.

---

