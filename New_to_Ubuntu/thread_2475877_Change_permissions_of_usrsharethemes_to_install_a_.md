---
title: "Change permissions of usr/share/themes to install a theme"
date: 2022-06-10
forum: New to Ubuntu
---

### Post by HerzeleidMeister on 2022-06-10
How do I change the permissions to the usr/share/themes directory so I can move new themes into that directory and access them with Gnome Tweaks? TIA!

---

### Post by #&amp;thj^% on 2022-06-10
> **HerzeleidMeister said:**
> How do I change the permissions to the usr/share/themes directory so I can move new themes into that directory and access them with Gnome Tweaks? TIA!

Best not do that, could cause system problems>>>to copy a theme use:
```
cp -r /location-of-theme/theme-name/ > /usr/share/themes/theme-name
```
Of course use sudo for admin rights.
I'm very accustom to just use this:
Example:
```
Download for your user

wget http://theme-url.zip -O ~/Downloads/theme.zip
unzip ~/Downloads/theme.zip -d ./themes
```

This downloads the theme only for your user. Does not require root.
Download for all users

```
wget http://theme-url.zip -O ~/Downloads/theme.zip
sudo unzip ~/Downloads/theme.zip -d /usr/share/themes/

```

---

### Post by Holger_Gehrke on 2022-06-10
You don't. You temporarily assume the identity of 'root' - the system administrator - to copy or move the directory containing the theme. On the command line you do this by prefacing the command with 'sudo' - for example 'sudo cp Chrome-OS-Dark-Marsala /usr/share/themes/'. 'sudo' will ask for your password. Don't be surprised when you don't see anything while typing it, that's a security measure for stopping shoulder surfers from knowing the length of your password.

 You can also do this in the file manager by using the 'admin' scheme. Hit ctrl-L in the file manager to get into the location bar then enter 'admin://' followed by the absolute path to the directory in which your theme directory is (and yes, that means you'll have something with a triple slash; you'll be asked for your password after you hit enter). Copy the directory, move to /usr/share/themes, and paste the directory.

Alternatively, if you don't have multiple users on your machine or you only want the theme available for one user, you can simply create a directory named '.themes' in your home directory (the dot at the beginning of the name means the directory will not be shown in the output of 'ls' or in the file manager unless you specifically ask for it; for 'ls' by giving the option '-a' (all) and by hitting ctrl-h in the file manager (this toggles showing hidden files) and move the theme there. Instead of '~/.themes' you can probably also use '~/.local/share/themes/'.

Holger

---

### Post by ActionParsnip on 2022-06-12
Use sudo when you need write access outside of your home. Don't go changing permissions. Your user has all the access it needs. You will break your system.

---

