---
title: "[SOLVED] How to run a command at login"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by styphon on 2008-05-25
I want my laptop to run this code at login:
```
xmodmap -e 'keycode 12 = 3 sterling'
```
However I have no idea what scripts run at login to get this code to execute, Please can someone tell me how I can get this code to run at login?

---

### Post by Jose Catre-Vandis on 2008-05-25
Put it in a script, then open up /etc/rc.local write the path to the script and save. Reboot and script should run on login.

So:

```
gedit myscript.sh
```

in gedit write as follows:
```
#! /bin/bash
xmodmap -e 'keycode 12 = 3 sterling'
```
save
Change permissions
```
sudo chmod +x ~/myscript.sh
```
then edit rc.local
```
sudo gedit /etc/rc.local
```
above the exit 0 line add the following replacing your user name as necessary:
```
/home/yourusername/myscript.sh
```
Restart

---

### Post by styphon on 2008-05-25
OK, that didn't work. It didn't run that command.

---

### Post by sdennie on 2008-05-25
I don't think xmodmap will run properly in rc.local because no DISPLAY variable has been set.  You should be able to go to System->Preferences->Session and add the command you want to the startup commands.

---

### Post by Jose Catre-Vandis on 2008-05-25
> **vor said:**
> I don't think xmodmap will run properly in rc.local because no DISPLAY variable has been set.  You should be able to go to System->Preferences->Session and add the command you want to the startup commands.

If that's the case, sorry, but you get the idea of how to run a script at boot, even if in this case xmodmap won't run :(

---

### Post by styphon on 2008-05-25
> **vor said:**
> I don't think xmodmap will run properly in rc.local because no DISPLAY variable has been set.  You should be able to go to System->Preferences->Session and add the command you want to the startup commands.

That's worked brilliantly. Thank you.

> **Jose Catre-Vandis said:**
> If that's the case, sorry, but you get the idea of how to run a script at boot, even if in this case xmodmap won't run :(
No problems. Useful if I want to run anything else though. When exactly in the boot process does that script run?

---

### Post by sdennie on 2008-05-25
It runs right at the end of the boot procedure.  Probably very near the time the login screen comes up.

---

### Post by styphon on 2008-05-25
> **vor said:**
> It runs right at the end of the boot procedure.  Probably very near the time the login screen comes up.

Ah, ok. I thought it was a login script. Is there one that runs at login that you can edit?

---

### Post by sdennie on 2008-05-25
I believe you can still create a script called .xinitrc that runs at login time but, it's probably better to go the System->Preferences->Session method just to keep everything consolidated in one place.

---

### Post by styphon on 2008-05-25
> **vor said:**
> I believe you can still create a script called .xinitrc that runs at login time but, it's probably better to go the System->Preferences->Session method just to keep everything consolidated in one place.

OK, thank you for your help.

---

### Post by sdennie on 2008-05-25
Glad to help.  :)

---

### Post by bthoward on 2008-06-05
So I have a script at ~/.mounts that looks like this

```
#!/bin/bash
mount /media/music

```
I call it mounts as I plan to later add more.

which is supposed to mount a share that I have added into my fstab but for some reason doesn't auto mount....

the fstab looks like:
```
sshfs#<user name>@<fqdn>:/var/lib/mythtv/music  /media/music   fuse   port=1234,user   0 0
```

The only thing I can think is that this isn't mounting because I don't have internet access until after login and after nm-applet links up the wifi.  However when I was running this share over CIFS it would mount automatically on login.  But this SSHFS line doesn't do that...  And for some reason when I put that script in my profiles area it doesn't work either... But if I run it in a terminal poof it mounts the drive right up...

---

