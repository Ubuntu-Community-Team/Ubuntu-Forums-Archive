---
title: "Save files permanently during a guest session"
date: 2010-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Gunnar Hjalmarsson on 2010-08-22
[INDENT][SIZE=3][COLOR=Red]*The tutorial [Customize guest session]("http://ubuntuforums.org/showthread.php?t=1566078"), which also covers several other ways to customize guest sessions, effectively supersedes this document.*[/COLOR][/SIZE]
[/INDENT]**[SIZE=4]Background[/SIZE]**

The guest session feature (package [gdm-guest-session]("http://packages.ubuntu.com/lucid/gdm-guest-session")) lets you start a temporary guest account with restricted privileges. Basically all changes are automatically deleted when a guest logs out.

It's nice to be able to hand over the computer to a friend or colleague who wants to check their mail, for instance, without a need to worry about security. However, *somewhere* I think they should be able to save file(s) which a regular user can work at further later on. Fortunately I noticed that they can - in the folder [FONT=Courier New][SIZE=2]/var/tmp[/SIZE][/FONT] - and I decided to let my guests know about that fact and share my solution here.

**[SIZE=4]Howto[/SIZE]**

**[SIZE=2]1. Create a dedicated folder[/SIZE]**

Even if it's possible to just use [FONT=Courier New][SIZE=2]/var/tmp[/SIZE][/FONT], creating a subfolder is probably a good idea.

**[FONT=Courier New][COLOR=DarkRed][SIZE=2]sudo mkdir -m 0777 /var/tmp/guest-data[/SIZE][/COLOR][/FONT]**


**[SIZE=2]2. A script for the purpose[/SIZE]**

This script inserts a desktop icon with a shortcut to [FONT=Courier New][SIZE=2]/var/tmp/guest-data[/SIZE][/FONT] and launches an info dialog:

```
#!/bin/bash

# exit if regular user
if [ $USER != 'guest' ]; then
    exit 0
fi

# shortcut to the guest-data folder
echo '
[Desktop Entry]
Name=Persistent guest data
Name[sv]=Filer som bevaras
Type=Link
URL=/var/tmp/guest-data
Icon=folder' > $HOME/$(gettext -d xdg-user-dirs Desktop)/guest-data_shortcut.desktop

# make the info dialog window become on focus
sleep 2

# info dialog
zenity --warning --title='Warning: Data will be deleted' --text=\
'Please be aware that this is an Ubuntu "Guest session".
It means that your data will be automatically deleted,
and possible altered settings will be reset when you log out.

There is an exception: Files that you save in the folder
/var/tmp/guest-data  will be preserved.'
```Take these steps to install it:
[LIST]
[*] [COLOR=DarkRed]**[FONT=Courier New][SIZE=2]sudo gedit /usr/bin/guest-session-mods[/SIZE][/FONT]**[/COLOR]
[*] Copy and paste the above code
[*] Save and quit the gedit window
[*] [COLOR=DarkRed]**[FONT=Courier New][SIZE=2]sudo chmod a+x /usr/bin/guest-session-mods[/SIZE][/FONT]**[/COLOR]
[/LIST]

[SIZE=2]**3. A desktop file**[/SIZE]

Finally we need a desktop file that invokes the script at the startup of each guest session.

```
[Desktop Entry]
Type=Application
Name=guest-session-mods
Exec=guest-session-mods
NoDisplay=true

```Take these steps to install it:
[LIST]
[*] [COLOR=DarkRed]**[FONT=Courier New][SIZE=2]sudo gedit /etc/xdg/autostart/guest-session-mods.desktop[/SIZE][/FONT]**[/COLOR]
[*]Copy and paste the above code and save
[/LIST]
  
**[SIZE=2]4. Test[/SIZE]**

Now when you start a guest session you should see this info dialog:

[IMG]http://gunnar.cc/img/guest-session-screenshot.png[/IMG]


**[SIZE=4]Comments[/SIZE]**

No system files are changed, and regular users are not affected. Consequently, if you change your mind, and/or would it not work to your liking, this is all there is to remove it:
[LIST]
[*] [COLOR=DarkRed]**[FONT=Courier New][SIZE=2]sudo rm -r /var/tmp/guest-data[/SIZE][/FONT]**[/COLOR]
[*][COLOR=DarkRed]**[FONT=Courier New][SIZE=2] sudo rm /usr/bin/guest-session-mods[/SIZE][/FONT]**[/COLOR]
[*][COLOR=DarkRed]**[FONT=Courier New][SIZE=2] sudo rm /etc/xdg/autostart/guest-session-mods.desktop[/SIZE][/FONT]**[/COLOR]
[/LIST]
 It's worth noting that this customizing approach can be applied if you want to display some other dialog and/or make other programs be launched at the start of a guest session.

I'll be watching this thread. Don't hesitate to post your questions or comments.

---

### Post by santhust on 2011-03-22
Thanks very much.:)
Could you also tell why can't I use sudo in the guess session, for example to copy some file into the "Persistent folder" [created using the above instructions]. Also, the folder I copied into the guest session in the folder guest-data, don't have permissions to edit them. Is this permission thing independent the task done here; in that case could you please tell how to take care of modify permission while copying some files/folders to the "persistent folder"?

---

### Post by Gunnar Hjalmarsson on 2011-03-25
> **santhust said:**
> Thanks very much.:)
You're welcome.

> **santhust said:**
> Could you also tell why can't I use sudo in the guess session, for example to copy some file into the "Persistent folder" [created using the above instructions].
The idea with the guest-session feature is to provide a session with restricted privileges, so sudo wouldn't fit in very well, would it? Besides I don't understand why you would need sudo to copy files into the folder. You did give it 0777 permissions, right?

> **santhust said:**
> Also, the folder I copied into the guest session in the folder guest-data, don't have permissions to edit them.
Files that you want to let others edit but the user who created them should better be given 0666 permissions.

> **santhust said:**
> Is this permission thing independent the task done here; in that case could you please tell how to take care of modify permission while copying some files/folders to the "persistent folder"?
As is stated above, this tutorial has been superseded by a [more complete tutorial on customizing guest sessions](http://ubuntuforums.org/showthread.php?t=1566078). Maybe you want to install the kit provided there; among other things it sees to it that files created by a guest are given 0666 permissions by default.

---

