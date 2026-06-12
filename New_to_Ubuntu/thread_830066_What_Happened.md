---
title: "What Happened ??"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by kdm on 2008-06-15
Hi all,

I just installed Ubuntu on my new laptop and all was going well until I changed my Gnome theme.  When I restarted the laptop, the login screens appear as normal, but when the computer attempts to start and show the desktop, it just freezes and a gayed out rectangle appears in the top left corner, but nothing else!  No toolbars, no wallpaper etc etc.

Can anyone help ?

Thanks

---

### Post by Biggy on 2008-06-15
go to System >Administartion >Hardware Drivers  and check Device drivers ,restart ubuntu.

---

### Post by kdm on 2008-06-15
Thats the problem though, I cant get at any settings, it just freezes before anything comes up

---

### Post by steveneddy on 2008-06-15
Try starting in safe mode.

---

### Post by Biggy on 2008-06-15
go inside of the pc and make sure that none of the cables have been disturbed, make sure everything is plugged in properly.

---

### Post by kdm on 2008-06-15
Tried safe mode and exactly the same thing happens ?

Nothing has came loose, its a laptop!

Am I looking at a full reinstall ?

---

### Post by durand on 2008-06-15
Umm, try running x from the command line. When it gets to the final stage, press Ctrl + Alt + F2
Enter your login details, then type:
```
sudo /etc/init.d/gdm stop
```
then:
```
startx
```
When it loads, go back to the command line with Ctrl + Alt + F2 and see if there are any errors.

---

### Post by NikoC on 2008-06-15
Well perhaps this might work (works for login themes)

I think when you download and install gnome themes they are stored in:
/usr/share/themes
So if you remember the name of the theme, try pressing ctrl + alt + f1 when your system has booted (this will get you in the command line)
Try deleting the folder of the theme you installed via:
sudo rm -r /usr/share/themes/installed_theme_name
Gnome should bootup using the default theme...

Can somebody confirm this?

---

### Post by durand on 2008-06-15
NicoC, themes are stored in the user's home folder at ~/.themes or ~/.icons unless they were installed system wide using apt-get.

---

### Post by durand on 2008-06-15
EDIT: I just thought of something. At the login screen, enter your username and password but **dont press enter after your password.** One of the options on the login screen is to change your session to failsafe terminal. Do that then run sudo users-admin and add a new user.

This user is only to check if things work right and that your own configuration is causing the problem.

---

