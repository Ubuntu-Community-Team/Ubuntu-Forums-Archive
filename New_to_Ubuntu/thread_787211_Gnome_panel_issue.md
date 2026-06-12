---
title: "Gnome panel issue"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by therealtombaker on 2008-05-08
Both my top and bottom panels in Gnome have disappeared. I can not make new ones. I have no idea what happened or how to fix it. Someone please help.

---

### Post by glennric on 2008-05-08
Try running
```
gnome-panel &
```
in a terminal.

---

### Post by therealtombaker on 2008-05-08
The only way I know how to access the terminal disappeared with the panels.

---

### Post by tamoneya on 2008-05-08
try alt-F2```
gnome-panel
```

---

### Post by therealtombaker on 2008-05-08
alt-F2 did nothing. I also tried to create a launcher and it did nothing.

---

### Post by glennric on 2008-05-08
Are you using compiz (Visual Effects) or metacity?

---

### Post by therealtombaker on 2008-05-08
Compiz

---

### Post by glennric on 2008-05-08
What happens when you right click on the desktop?  Do you get the usual menu?  Doesn't that have an Open Terminal option in it?

---

### Post by therealtombaker on 2008-05-08
It does not have an open terminal option. I'm afraid that this is FUBAR and am currently backing everything up to my external hard drive in case I need to re-install Ubuntu.

---

### Post by glennric on 2008-05-08
Something is really messed up with your system.  Have you tried rebooting or is this on a fresh boot?

---

### Post by therealtombaker on 2008-05-08
I have tried both ctrl-alt-backspace and rebooting. Every time it comes back up without the panels.

---

### Post by tamoneya on 2008-05-08
does it pop up if you hit ctrl-alt-backspace (this will restart X and will cause screen to go black but it will come back)
EDIT: never mind

---

### Post by glennric on 2008-05-08
Have you checked to make sure that gnome-panel is installed?

Try hitting Ctrl-Alt-F1.  Then log in and type ```
sudo apt-get install gnome-panel
```

---

### Post by therealtombaker on 2008-05-08
It worked, but with a couple of errors. My panels are both back except for the GWeatherApplet, where it stated > The panel encountered a problem while loading "OAFIID:GNOME_GWeatherApplet"  and the System Monitor where it stated > The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet" Any ideas on how to fix it?

---

### Post by glennric on 2008-05-08
Try removing them from the panel and adding them again.

---

### Post by therealtombaker on 2008-05-08
Already tried that. It gives me that message every time I try to add them back. Would restarting help, or do you think I might be missing a package that supports those applets?

---

### Post by glennric on 2008-05-08
Make sure that the package gnome-applets is installed.

---

### Post by therealtombaker on 2008-05-08
It worked. Thank you so much for all of your help. It looks like evrything is fixed now.

---

### Post by crjackson on 2008-05-08
Do you have proposed updates enabled in the repositories?  Did you recently install a bunch of updates.

I did and got the same problem.  I restored my system to the state just before the updates and it fixed the problem.  Then I turned off proposed updates and got only the official updates and it's working fine.

It is a Bug...

---

