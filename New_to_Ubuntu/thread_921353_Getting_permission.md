---
title: "Getting permission"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-09-16
I downloaded some themes onto my desktop but now I want to move them into the 'themes' folder.
However, when I copy and go to paste them it says I don't have permission..yet I am the admin and the only account on this laptop.

What am I doing wrong?

cheers

---

### Post by Idefix82 on 2008-09-16
Open the terminal, change into the desktop folder and type in
```
sudo cp "file name or folder name of the themes" "full path to themes folder"
```
replacing the stuff in "" as appropriate.
Edit: Just a quick explanation: although you may be the only user on the computer and thus with your windows background you would expect to have all permissions, Linux has a clever way of protecting your system from viruses and other attacks: whenever you try to do something which could harm your system (like copying files into a folder, which is important for proper functioning of the system) you need to confirm that it's you and not some bad script. In the terminal you have to start a command with "sudo" for it to ask you for your password. You can also open the file browser with all priveleges enabled by typing
```
gksudo nautilus
```
and then you will be able to do what you wanted in  the file browser but that's less safe since now any script can do anything in this file browser window.

---

### Post by northern lights on 2008-09-16
Most likely the folder you're trying to copy to is owned by root and you'd have to assume superuser rights.
For general purposes [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") might be a worthy read.

However, are you certain the downloaded themes need indeed be copied to where you were trying?

What themes are these?

---

### Post by iaculallad on 2008-09-16
Or you could use:

```
gksudo nautilus
```

A new nautilus window will open giving you 'root-like' privilege enabling you to copy and paste folders/items without restriction.

---

### Post by drsaamah on 2008-09-16
on ubuntu (well, actually all linux OS's as far as I know) no user is actually administrator.  Only the "root" user is administrator.  By default, you cannot actually log in as root user in Ubuntu (this is a security measure).  For most administrative tasks you can give authority to run a certain task *as* an administrator (you see this when you run update manager and you are prompted to provide a password).
So in order to complete this tasks, you must turn to the terminal...
Open a terminal.  run the command:
```
sudo cp ~/Desktop/NAME_OF_THEME_PACKAGE /usr/share/themes
```
It will then prompt you for your administrative password, and that should be the end.
Cheers!

---

### Post by nothingspecial on 2008-09-16
The easiest way might be to right click on your desktop. Click change desktop background. Click on the Themes tab. Click install and browse to the downloaded files.

---

### Post by Mornedhel on 2008-09-16
If it's a standard theme from art.gnome.org or gnome-look.org, you can also start the Appearance configuration dialog, click "Install new theme", select your .tar.gz file, wherever it is, and it will be installed properly. No need to move into themes by hand.

---

### Post by highlyevolved on 2008-09-16
thanks!

---

