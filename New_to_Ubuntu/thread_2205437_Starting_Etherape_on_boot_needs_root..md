---
title: "Starting Etherape on boot needs root."
date: 2014-02-13
forum: New to Ubuntu
---

### Post by blukami on 2014-02-13
I want to Etherape start on boot up but to do it right it needs root privileges. How do I do it right so I don't have to start it myself in terminal with sudo?

---

### Post by ian-weisser on 2014-02-14
It's difficult for two reasons.

The first is the difference between boot and login. Until a user logs in, NO applications that require a display can be started. There is no display for the application to output to, and that's usually a fatal error. All boot applications are headless - they don't require a display. So you either need Etherape to start at login (instead of boot), or you need to find a displayless network monitor to start at boot (instead of login).

The second is the difference between the root user and the ordinary user. That's where privileges come in, and there are a couple ways to fix it.
- You can edit the sudoers file using the "sudo visudo" command. This will make it possible for your script to launch "sudo etherape" as a normal start-at-login application without a password.
- Or you can learn about the dbus interprocess communication sockets, and use a dbus-send command to launch the application. dbus takes care of the permissions for you.
- An even more complicated way is to use a Unix socket and upstart-socket-bridge job to trigger etherape. Not a way I would recommend, since then any user can run Etherape, but it's certainly possible.

---

### Post by ian-weisser on 2014-07-22
Here's how to change the settings in Ubuntu 14.04 to create an Etherape (as root) launcher in Unity that won't require a password.
It has ONLY been tested with 14.04. It probably won't work if you're not using 14.04.

It requires a minor edit to the /etc/sudoers file, and minor edits to two .desktop files. It's easy to undo if you change your mind.

1) Edit the sudoers file to prevent asking for password
```
$ sudo visudo
```

At the bottom of the file, add one line. 

```
account_name hostname = NOPASSWD: /usr/bin/etherape
```
account_name is your login account name (Fred, Jane, Dog, whatever)
hostname is your machine name as shown in /etc/hostname (My_Laptop, pwned, Gandalf, etc.)

Do a CTRL+X to exit, and hit Y to confirm the exit.
The visudo program will check your changes.
If visudo is happy with your changes, it will print no output, but simply return you to a command prompt.

*Look carefully at the screen*. If visudo shows an error, type 'edit' and go right back in to fix the error. If you don't know how to fix the error, delete your added line and save. You MUST NOT exit with a broken sudoers file - a broken sudoers file is 100% guaranteed to break your system! It's very important that you pay close attention to any error messages visudo prints when you try to exit.



2) Test: Open a NEW terminal window and try 'sudo etherape'. It should no longer ask for a password.

If you get sudo errors instead, you have broken your system! Stop! Save all your data! Reboot into a recovery console (since you cannot use sudo) and edit /etc/sudoers to remove your changes. Open a new thread in this forum and ask for help on how to do this!



3) OPTIONAL: Once visudo approves of my syntax, I prefer to put my working /etc/sudoers changes in a separate file in /etc/sudoers.d/



4) Edit the etherape-root .desktop file

I use nano to edit. You can use vi or emacs or gedit or wnatger you wish.
```
sudo nano /usr/share/applications/etherape-root.desktop
```

```
Name=EtherApe (as root)
Type=Application
Categories=GNOME;System;Network;
Comment=Graphical Network Monitor
Comment[es]=Monitor Gráfico de Red
#TryExec=su-to-root                         <-- Comment out
#Exec=su-to-root -X -c /usr/bin/etherape    <-- Comment out
Exec=/usr/bin/sudo /usr/bin/etherape        <-- Add line
Icon=etherape
Terminal=false
```


5) Edit the etherape (user) .desktop file to hide it. We don't want to delete it; the package manager will expect it to be there.

I use nano to edit. You can use vi or emacs or gedit or wnatger you wish.
```
sudo nano /usr/share/applications/etherape.desktop
```

```
#[Desktop Entry]                  <-- Comment out
Version=1.0
Encoding=UTF-8
Name=EtherApe
GenericName=EtherApe
Comment=Graphical Network Monitor
Comment[es]=Monitor Gráfico de Red
Exec=etherape
Terminal=false
Type=Application
Icon=etherape
Categories=GNOME;System;Network;
```


6) Open Unity's Dash. 
Close any existing search. 
Search for Etherape. There should be only one option now: Etherape (as root). 
Open it. It should show all interfaces without requiring a password or prompting an error.
Lock it to the Launcher. Close it.
Open it again from the launcher. It should work

---

