---
title: "Users administration"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Carlo Franceschi on 2012-08-25
Dear all,
I'm not a new linux user (I started my linux experience in 1996) and I use
Ubuntu from his version 9.04.

Now,
I have installed Ubuntu 12.04 after downloading the 64 bit iso image from [http://www.ubuntu.com/](http://www.ubuntu.com/)

After the installation I have created a new user. In this way I can connect with the first user (created during the installation) and with the second one.
All works fine.

After that I have downloaded and applied all the software update required by the system.

I have created a new user (the third).
With this user I can't connect.
When I try to connect no error appear.
The screen change to black and after a few second login screen appears another time.

The home directory of the new user contain just these files:

```
carlo@carlo-desktop:/home/utente1$ ls -la
totale 44
drwxr-xr-x 3 utente1 utente1 4096 ago 25 13:47 .
drwxr-xr-x 5 root    root    4096 ago 25 13:46 ..
-rw------- 1 utente1 utente1   41 ago 25 13:47 .bash_history
-rw-r--r-- 1 utente1 utente1  220 ago 25 13:46 .bash_logout
-rw-r--r-- 1 utente1 utente1 3486 ago 25 13:46 .bashrc
drwx------ 2 utente1 utente1 4096 ago 25 13:47 .cache
-rw-r--r-- 1 utente1 utente1   34 ago 25 13:47 .dmrc
-rw-r--r-- 1 utente1 utente1 8445 ago 25 13:46 examples.desktop
-rw-r--r-- 1 utente1 utente1  675 ago 25 13:46 .profile

```

Do you have any suggestion?

Best regards

---

### Post by grahammechanical on 2012-08-25
Please confirm that you can still login and go to a working desktop as the first user and the second user.

If you cannot do this then the software that creates the desktop must be faulty.

If you can login as first user you will have administrator privileges. So, you can delete the third user using System Settings>User Accounts. And then try to create the third user account again. It might be good if you shut down and reboot before trying to recreate this account. The operating system will then read its boot files again.

You may of course be putting in an incorrect password. I am not sure if 12.04 gives a warning if the password is incorrect. Check that the password is correct and that the caps lock key is not on.

You will say that you have already done this but we need to confirm that these things have been done. We have all tripped up over silly little things.

Regards.

---

### Post by steeldriver on 2012-08-25
You can also check whether it is an authentication problem or an X-session startup problem by trying to log in as utente1 at one of the virtual terminals (e.g. Ctrl-Alt-F1)

You can return to the graphical session using Ctrl-Alt-F7

---

### Post by Carlo Franceschi on 2012-08-25
For "grahammechanical":


[LIST]
[*]yes I confirm that I can still login and go to a working desktop as the first user and the second user
[*]I have already tried to delete and re-create new users but they dont work
[*]If I type a wrong password the system promt an error
[/LIST]
For "steeldriver": I can authenticate with the third user via virtual terminal but if, after the authentication,  I press Ctrl-Alt-F7 I ever obtain the login-screen


Concerning x-session please note that at the first time (after the installation) I had only 2 display  resolution (800x600 and 1024x76) To work using my monitor resolution (1680x1050) I have prepared the following script: 



```
#!/bin/sh
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 1680x1050_60.00
xrandr --output VGA1 --mode 1680x1050_60.00
```The script is located in /usr/share and it is called by lightdm.conf:


```
[SeatDefaults]
user-session=ubuntu.desktop
greeter-session=unity-greeter
[SIZE=2]**greeter-setup-script=/usr/share/lightdmxrand.sh**[/SIZE]

```Could I resolve the problem using a different gdm instead of lightdm?

---

### Post by steeldriver on 2012-08-25
Since other users can login to the graphical session, I doubt that the problem is with any global configuration settings

The only file in /home/utente1 that appears to relate to your new user's graphical session specifically is the .dmrc file - maybe that one got corrupted (or specifies a non existent session? although I would think that the system should have a fallback session). You could rename / delete / copy one of the working users' .dmrc files to see if that helps. Sorry that's about all I can suggest.

BTW what method are you using to create the new user accounts? Are you copying any home directory contents from old accounts?

---

### Post by Carlo Franceschi on 2012-08-25
I've tried to move the .dmrc file from a working user but the problem still remain.

To create new account I've used the tool "User account", no files copied.

---

### Post by Carlo Franceschi on 2012-08-26
I have switched from lightdm to gdm and now it works!
I can now connect with all users.

Many thanks.

---

