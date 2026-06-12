---
title: "Can't see any themes (screenshot)"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by helil on 2012-05-17
I am a newbie.

I can't see any themes to apply at the "appearance" application (check the screenshot).
At Synaptic, I can see that I have a lot of themes installed, such as "ubuntustudio-gdm-theme" or "plymouth", but I can't see how I could apply or edit anything.

Any help?

---

### Post by Lisiano on 2012-05-17
That's... Unusual?
We can try reseting gnome if you wish. To make stuff easier, here is a script that should do it for you, but it must be run from inside an app called [screen (Click to install)]("apt://screen") or from a TTY.
Open a terminal (Ctrl+Alt+T) and type in
```
gedit gnome_reset.sh
```
Then copy-paste this code in the editor.
```
#!/bin/sh
sudo service lightdm stop
cd
mkdir -p Gnome_Backup/.config
mv .gtk* .gconf .gnome2 Gnome_Backup/
mv .config/dconf .config/compiz-1 Gnome_Backup/.config/
sudo service lightdm start
```
Save it and run this command
```
screen
```
Press enter
```
sh ~/gnome_reset.sh
```
It will show you this line
```
[sudo] password for helil:
```(Or whatever your username is)
Now type in your password, don't worry, the fact you don't see it nor any asterisks is fine. Now, the second you press enter, all your open apps will close instantly and any unsaved work will be gone, I warned you.

After the script finishes, it should show you the login screen, if not, then reboot and we will do it the TTY way.
Now, after you log back in, you should notice that almost everything was reset, including some settings.

[SIZE="1"]Note to other helpers: I don't remember if Gnome saves it's configs on logout if they are missing so I kill it first, reason for killing lightdm is so the user won't have to use a TTY, screen for the same reason.[/SIZE]

---

### Post by helil on 2012-05-18
Thanks for your response, Lisiano.

I did it all and got this message back:

Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?
mv: invalid option -- 'r'
Try `mv --help' for more information.
mv: invalid option -- 'r'
Try `mv --help' for more information.
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?

---

### Post by Lisiano on 2012-05-18
My fault. Left out some important bits and added an unneeded argument. Fixed. Let's do it the TTY way then. (Or alternatively, try the edited code pasted above again)
Log out of your user and switch to a TTY (Ctrl+Alt+F1-F6)
Now type in your username then the password, like sudo, it will not be visible.
Now type in this
```
mv .gtk* .gconf .gnome2 Gnome_Backup/
mv .config/dconf .config/compiz-1 Gnome_Backup/.config/
```
I recommend you write it down or view it from a phone/tablet/laptop/2nd PC while you type and use Tab to autocomplete. Now after that, type ```
exit
``` and press enter. You will be logged out of the TTY and now you need to get back to the GUI (Ctrl+Alt+F7) and log back into your normal user.

---

### Post by helil on 2012-05-25
Hi Lisiano, thanks again.
I did it and *something* happened. I guess I did restart Gnome: my custom wallpaper is gone and I got rid of the "high contrast" I was stuck with, but I still can't find any theme to apply at the "appearance" app.
best,

---

### Post by pablo180 on 2012-05-25
It is probably the first thing that you tried but just in case you haven't; have you tried opening the software centre and searching for Light Themes and installing them?

That should give you the two default themes, Ambiance and Radiance, if you don't already have them.

---

### Post by helil on 2012-05-29
Hello guys, thanks for your help.
First, I installed Gnome (or reinstalled, really can't understand things) from Ubuntu Software Center. After restart, I got a default theme - Adwaita - and things looked better. After that I could install Light themes from synaptic.
I guess I'm marking this "solved"...

Thank you

---

