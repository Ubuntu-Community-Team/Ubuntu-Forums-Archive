---
title: "Script : CTRL-ALT-F1"
date: 2007-03-10
forum: Programming Talk
---

### Post by michellembrodeur on 2007-03-10
I am writing a script for auto installing nvidia drives.

But when the command of 
sudo /etc/init.d/kdm stop       
or
sudo /etc/init.d/gdm stop 
is run the screen go blank with a cursor on the top left corner and you have to press
CTRL-ALT-F1 to get back to the screen.

Do do you program CTRL-ALT-F1 into a script fill to run.

thanks all

---

### Post by lnostdal on 2007-03-10
try `nohup' or something similar to avoid this

---

### Post by hod139 on 2007-03-10
You can probably ask [tseliot]("http://ubuntuforums.org/member.php?u=19388") what he did.  He maintains a repository with the latest drivers: [[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=19388")[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by ssam on 2007-03-11
have a look at chvt (change virtual terminal).

if you log in on text terminal 1 (CTRL+ALT+F1), and then run
```
chvt 2
```
it will switch
```
chvt 7
```
switches back to the desktop

but from the GUI in a gnome-terminal
```
chvt 1
```
does not work.

---

