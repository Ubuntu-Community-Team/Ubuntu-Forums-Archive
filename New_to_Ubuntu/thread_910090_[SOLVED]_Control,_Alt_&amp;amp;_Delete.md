---
title: "[SOLVED] Control, Alt &amp;amp; Delete"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by unknown user on 2008-09-04
[FONT="Verdana"][COLOR="Blue"]In Ubuntu do you have the Control, Alt & Delete function (or something similar to it?[/COLOR][/FONT]

---

### Post by kpkeerthi on 2008-09-04
What do want to happen when you press ctrl + alt + del? Lock screen?

---

### Post by Joeb454 on 2008-09-04
You could set the key-combo to be a shortcut for the Gnome system monitor

---

### Post by porchrat on 2008-09-04
You could take a screenshot of a blue screen of death and have it bring that up everytime you pressed ctrl + alt + del.

Would make me feel right at home that would.

---

### Post by billgoldberg on 2008-09-04
The system monitor is in "system -> administration -> system monitor".

Use ctrl + alt + backspace to restart the xserver.

You can set anything to ctrl + alt + del if you want to.

Gnome has pretty limited keyboard shorcuts, so use an app called "xbindkeys" to do so.

---

### Post by jemate18 on 2008-09-04
> **unknown user said:**
> [FONT="Verdana"][COLOR="Blue"]In Ubuntu do you have the Control, Alt & Delete function (or something similar to it?[/COLOR][/FONT]

Is this like showing a "task bar" or GNOME-SYSTEM-MONITOR? Check the above post

---

### Post by kramer65 on 2008-09-04
Have a look here: [https://answers.launchpad.net/ubuntu/+question/19234](https://answers.launchpad.net/ubuntu/+question/19234)

I've alwaqys wanted to do that as well but couldn't find it either. Now I just did a search and found the above.. :-)

Good luck!

---

### Post by unknown user on 2008-09-04
[FONT="Verdana"]All I wanted to do really was system monitor, be able to end processes and things like that.  Was not sure if this could be done in Ubuntu

Cheers for the link, will have a look at it shortly[/FONT]

---

### Post by ashmew2 on 2008-09-04
> **porchrat said:**
> You could take a screenshot of a blue screen of death and have it bring that up everytime you pressed ctrl + alt + del.

Would make me feel right at home that would.

omg...owned..

---

### Post by rossjman1 on 2008-09-04
sudo apt-get install xbindkeys xbindkeys-config
then run xbindkeys-config to make the shorcuts.
You then need to go to System > Preferences > Sessions and add "xbindkeys" to automatically start up with gnome.

---

### Post by unknown user on 2008-09-15
rossjman1 I did the sudo line and all was OK, I tried to 'then run xbindkeys-config to make the shorcuts.' but I am lost here, how do I do this?

---

### Post by scorchgeek on 2008-09-15
In order to end processes, you have to use the top terminal command. For a system monitor, you can choose System > Administration > System Monitor.

---

### Post by nowshining on 2008-09-15
or better yet ctrl+alt+f1 - f6 to  get a tty - type killall -9 appname or just killall appname to kill gracefully and then ctrl+alt+f7 to get back to the GUI,

as for top use htop, sudo apt-get install htop :)

---

### Post by unknown user on 2008-09-30
Cheers, kramer65 I followed the link that you provided and the two command lines at the bottom worked a treat.  Now when I click Control, Alt & Delete the system monitor comes up like I wanted.

---

### Post by walkingthecow on 2008-09-30
at terminal "ps -ef | grep process" then kill PID, or kill -9 PID to end the process. Also, with Linux you can do "ps aux". That is the best way to end a hung process.

---

### Post by MrFSL on 2008-09-30
> **porchrat said:**
> You could take a screenshot of a blue screen of death and have it bring that up everytime you pressed ctrl + alt + del.

Would make me feel right at home that would.

MY GOD thats harsh!

---

### Post by Dojan5 on 2008-09-30
> **unknown user said:**
> [FONT="Verdana"][COLOR="Blue"]In Ubuntu do you have the Control, Alt & Delete function (or something similar to it?[/COLOR][/FONT]

Nope...
Everytime I kill a process I use in the terminal
```
killall process-name
```

---

