---
title: "Having problems running Nautilus as root"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by matti123456 on 2016-05-12
I am using 'sudo nautilus', but i am getting errors.

```
(nautilus:2266): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Initializing nautilus-dropbox 2.10.0
sys:1: PyGIWarning: Nautilus was imported without specifying a version first. Use gi.require_version('Nautilus', '3.0') before import to ensure that the right version gets loaded.
/usr/share/nautilus-python/extensions/nautilus-admin.py:18: PyGIWarning: GConf was imported without specifying a version first. Use gi.require_version('GConf', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import Nautilus, GObject, GConf, Gtk, GLib

** (nautilus:2266): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
```

---

### Post by vasa1 on 2016-05-12
If you're new to Ubuntu (and to Linux), running file managers (or most anything) as root isn't really recommended.

Could you tell us why you wish to do so?

Also, please run just *nautilus* in a terminal and tell us what happens. Does the program appear to run normally? If that is so, you can discount whatever appears in the terminal. See [http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications](http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications) for why.

If you really want to run Nautilus as root, try
*sudo -H nautilus*
or
*pkexec nautilus* [SUP]***[/SUP]
or, if you have gksudo installed,
*gksudo nautilus*

[SUP]***[/SUP]I think that this requires that a suitable policy file exists.

---

### Post by matti123456 on 2016-05-12
> **vasa1 said:**
> If you're new to Ubuntu (and to Linux), running file managers (or most anything) as root isn't really recommended.

Could you tell us why you wish to do so?

Also, please run just *nautilus* in a terminal and tell us what happens. Does the program appear to run normally? If that is so, you can discount whatever appears in the terminal. See [http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications](http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications) for why.

If you really want to run Nautilus as root, try
*sudo -H nautilus*
or
*pkexec nautilus* [SUP]***[/SUP]
or, if you have gksudo installed,
*gksudo nautilus*

[SUP]***[/SUP]I think that this requires that a suitable policy file exists.

It does not seem to be problem with Nautilus[I]. [I]'Sudo -H nautilus' command worked, but it did not fix the problem.

I am trying to replace desktop-login.ogg with different sound file, but as soon as i replace desktop-login.ogg it reverts back to the default file. I used this guide.(it should work for Ubuntu 16.04 as well.) [https://ubuntu-mate.community/t/how-to-activate-ubuntu-login-sound/677](https://ubuntu-mate.community/t/how-to-activate-ubuntu-login-sound/677)

[/I][/I]It is not a big deal, my life won't derail, if i can't find solution to this. :P

---

### Post by mastablasta on 2016-05-13
> Another desktop manager in use; desktop window won't be created

make sure you don't have anything else opened. 

as for the second part make sure you are swithing the correct file. when you run nautilus as root you change the user, so home is not your user's home anymore.

furthermore - i can't see any use of sudo in the guide you linked.  you install an app for changing sounds if it's not already installed and then change the sound is how i udnerstand it.

finally, this is the issue i have with gnome. a thing like this should be available via GUI in system settings. although maybe it is, and we are both looking at the wrong guide.

---

### Post by Bucky Ball on 2016-05-13
You should be opening GUIs as root with gksudo, not sudo.

> gksudo nautilus

Might not make any difference, but use that, not sudo.

I will reiterate what has been said previously: running file managers as root is generally to be avoided. Once you've done what you need to do in there, close out. Don't hang about in there. You can cause some SERIOUS breakage with one false move (and as it looks pretty much the same as root as when normal user, easy to forget you are in there as root if you hang around).

---

### Post by vasa1 on 2016-05-13
> **Bucky Ball said:**
> ... (and as it looks pretty much the same as root as when normal user, easy to forget you are in there as root if you hang around).
I have visibly different gtk themes for user and when running  with gksudo.  That helps. But I can't remember the last time I used any GUI program other than Synaptic ;)

---

### Post by buzzingrobot on 2016-05-13
Looking at that wiki page, it seems the actual sound file you want played could be installed anywhere.  For example, somewhere in your home folder.  That would avoid all the hassle of trying to run Nautilus as root.

Just provide a full path to the file in the startup tool.  I.e., if the sound file is in the Music folder in user Matti's home directory, the full path would be "/home/matti/Music/sound_file.ogg".  Ue the "Edit" function in the startup tool and use that to replace the "/usr/share/...." path that appears in the wiki's example.  (FYI:  Case -- captialization -- matters here:  /home/matti" and /home/Matti" are not the same.)

You shouldn't need to run Nautilus as root to copy the sound file to your home folder.

Give it a try.

---

### Post by grahammechanical on 2016-05-13
> *[I]as soon as i replace desktop-login.ogg it reverts back to the default file. *[/I]

Just a small point. Make sure that Nautilus is not creating a hidden backup file that is still being used by the system. Hidden backup files will have the same name as the original file but have the tilde character ( ~ ) as a prefix. Removing the hidden backup file will force the system to use the only file with that name.

Reggards.

---

### Post by matti123456 on 2016-05-13
> **mastablasta said:**
> make sure you don't have anything else opened. 

as for the second part make sure you are swithing the correct file. when you run nautilus as root you change the user, so home is not your user's home anymore.

furthermore - i can't see any use of sudo in the guide you linked.  you install an app for changing sounds if it's not already installed and then change the sound is how i udnerstand it.

finally, this is the issue i have with gnome. a thing like this should be available via GUI in system settings. although maybe it is, and we are both looking at the wrong guide.

I was actually using different guide that was on youtube, i figured that nobody would bother watching 10-minute video, so i found text guide. Didn't notice until you mentioned it, but the guide i linked only showed how to activate the login sound and not how to replace the default file.

> **Bucky Ball said:**
> You should be opening GUIs as root with gksudo, not sudo.



Might not make any difference, but use that, not sudo.

I will reiterate what has been said previously: running file managers as root is generally to be avoided. Once you've done what you need to do in there, close out. Don't hang about in there. You can cause some SERIOUS breakage with one false move (and as it looks pretty much the same as root as when normal user, easy to forget you are in there as root if you hang around).

This one did the job! Bit suprised that it worked, not that i am expert on Ubuntu.

---

### Post by Bucky Ball on 2016-05-13
Good news. ;)

Please mark thread as solved (see second link in my signature or Thread Tools at top right).

---

