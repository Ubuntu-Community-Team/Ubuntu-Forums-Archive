---
title: "nvidia-settings ERROR: Unable to remove old X config backup file '/etc/X11/x"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by LarryJ2 on 2008-05-12
If you are trying to extend your desktop across two monitors (which nvidia calls twinview) and you receive the following error message while in nvidia-settings,

> ERROR: Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

exit "nvidia-settings",   then make a backup xorg.conf then try running "nvidia-settings" with administrators privileges as shown below.

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.mybackup
sudo nvidia-settings
```

Twinview is selected (and configured) from the "X Server Display Configuration" left menu selection in "nvidia-settings".

Nothing happens when you try to invoke nvidia-settings?  Try
```
sudo apt-get install nvidia-settings
```

Note: These steps only apply if you have an nvidia based display adapter and are using the nvidia-glx-new driver and nvidia-settings is installed.

---

### Post by allandelmare on 2009-05-23
For anyone searching a solution to this error message, the given solution applies (even if you aren't trying to use twinview)

All I did was create a bad backup, and it started giving me this error - I'm not trying to use twinview. Just use the given code and it will clear it up (Ubuntu Jaunty 9.04 x64)

---

### Post by LarryJ2 on 2009-05-24
I'm glad my post was useful.   Now about three years into Linux (Fedora and now Ubuntu),  I can understand why the error message was created.  Try this on your PC (from within a Applications->Accessories->Terminal)

```
ls -al /etcX11/xorg.conf
```
If the response is 
> lj@dell:~$ ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 2335 2008-07-03 15:41 /etc/X11/xorg.conf


then only the owner root (or a user with administrators privileges) can write (make changes to) the file /etc/X11/xorg.conf.  So no wonder that starting nvidia-settings without  "sudo" doesn't work. That is```
sudo nvidia-settings
``` runs and allows modifications.```
nvidia-settings
``` doesn't allow modifications or the backup file to be created in this directory.

Since you are likely invoking nvidia-settings from Sytem->Administrator->NVidiaServer Settings,  one would think that the nvidia's configuration utility is invoked with root or administrators privileges.  But alas,  that apparently doesn't happen.  So if the utility tries to rewrite /etc/X11/xorg.conf,  it fails and prompts the referenced error message.  

Discussion of sudo lives here:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  There I read:
> Graphical sudo

You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).

Examples:

gksudo gedit /etc/fstab
or in this instance
```
gksudo nvidia-settings
```
or if you are using the KDE desktop rather than gnome default```
kdesudo nvidia-settings
``` .

Message to nVidia---  It would be nice if your error message said "Unable to write to /etc/X11/xorg.conf or to it's directory.  Invoke nvidia-settings with administragtors (root) privileges".  Their current error popup message was not helpful.

---

