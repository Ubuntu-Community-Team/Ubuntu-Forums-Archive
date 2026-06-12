---
title: "sudo shutdown launcher (ubuntu 12.04)"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by pyro-lsf on 2014-02-18
Hi,   I just (finally^^) succeeded in creating a launcher desktop icon for       sudo shutdown -h now   (i need that because standard shutdown function doesnt shut down the fans...)  and it works. when i click the icon, the terminal pops up and asks for my password to verify shutdown.      now what i actually wanted is several launchers for      sudo shutdown -h +X    for example +30 to shutdown in half an hour.      now if i click that icon, nothing happens..     i can't see why 'shutdown now' should work and 'shutdown +X' shouldn't....  any ideas?

---

### Post by Dave_L on 2014-02-18
Just a wild guess.  Could it be due to the sudo timeout value, which defaults to 15 minutes?

---

### Post by pyro-lsf on 2014-02-20
no idea, since i'm a total newcomer to ubuntu =)

---

### Post by Dave_L on 2014-02-20
Each launcher should be contained in a .desktop file in the ~/Desktop folder.

Could you post, as text, a shutdown launcher that works and one that doesn't? Please use [ code ] .. [ /code ] tags (without the spaces). To view the text:

```
cat ~/Desktop/xxxx.desktop
```

---

### Post by coldcritter64 on 2014-02-20
> **pyro-lsf said:**
> ....   for example +30 to shutdown in half an hour.      now if i click that icon, nothing happens..     i can't see why 'shutdown now' should work and 'shutdown +X' shouldn't....  any ideas?

After clicking on your delayed shutdown button, the delay in minutes being what you add with the +30, half an hour in your case, before anything will apparently happen with a sudden shutdown.


Run the code,
```
ps -A | grep shutdown 
```
**before** you press your delayed shutdown button, and you will get **no** response from the terminal.

Press the delayed shutdown button and then run the code above, and you should get a response like,
```
yeti:~ $ ps -A | grep shutdown
16409 pts/1    00:00:00 shutdown
```This lets me know the command actually has worked, it's process is running.

Check if yours is running with that code, and also if you have the launcher set up to run your command in the terminal (it sounds like the 1st launcher is ok that way, check the second launcher for that setting).

Edit: if you ever need to cancel a queued shutdown command,
```
sudo shutdown -c
```
will cancel it for you.

---

### Post by pyro-lsf on 2014-02-21
sudo shutdown -h now:
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[de_DE]=gnome-panel-launcher
Name[de_DE]=Shutdown now
Exec=sudo shutdown -h now
Name=Shutdown now
Icon=gnome-panel-launcher

```

sudo shutdown -h +30
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[de_DE]=gnome-panel-launcher
Exec=sudo shutdown -h +30
Name[de_DE]=Shutdown +30
Name=Shutdown +30
Icon=gnome-panel-launcher

```

in the second code it says terminal=false, maybe herein lies the problem?


```
ps -A | grep shutdown
```

nothing happens there...


EDIT:

just changed it into terminal=true, now it works =)

while i'm on it, is it possible to create a shutdown +x launcher, so that the console would ask me for a time parameter to enter.
and secondly, is there any way to integrate the password into the launcher or having it perform the shutdown without asking my password every time over?

---

### Post by coldcritter64 on 2014-02-21
The terminal asking for a time input would require some scripting, someone else will need to help you with that.

For running a sudo command without the password (use with caution, you can seriously compromise a machine if this is done with the wrong commands)
... an info link to a similar question on AskUbuntu. [http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

I would recommend you read also; [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for general information regarding sudo and its use.

---

