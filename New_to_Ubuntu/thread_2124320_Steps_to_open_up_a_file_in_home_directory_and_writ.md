---
title: "Steps to open up a file in home directory and write in a command in it"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Nmalik31 on 2013-03-10
HI:

I am a beginner in Ubuntu and need easy **clear steps/commands that can open a file named '.xinitrc' which is in Home directory and also want to write in a command-line in this file.  How will I do it.  Any help will be highly appreciated.**

---

### Post by Cheesemill on 2013-03-10
The .xinitrc file doesn't exist in a standard Ubuntu installation so you'll have to create it yourself.

Fire up your text editor (gedit if you are using Ubuntu) and write what you need then just save the file as .xinitrc in your home directory.

---

### Post by Nmalik31 on 2013-03-11
Kinfly tell me what command to use to open text editor using "Gedit" and also what command to save the file.  Many thanks.

---

### Post by Cheesemill on 2013-03-11
Which version of Ubuntu are you using?

If you are using the normal desktop version then to open gedit just press the super (Windows) key,  type gedit, and then click on the icon that appears.
To save the file click on File > Save on the menu bar at the top of the screen.

---

### Post by schragge on 2013-03-11
Be aware that commands in *.xinitrc* only get executed for X sessions manually started from command line with [startx]("http://manpages.ubuntu.com/manpages/precise/en/man1/startx.1.html"). If you start your GUI through a display manager ([uwiki]LightDM[/uwiki]), either put them into *.xsessionrc* instead or autorun your script from */etc/lightdm/lightdm.conf*

---

