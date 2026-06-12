---
title: "[SOLVED] persistance of environment variables"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ceclauson on 2008-07-27
Hello!

I'm a bit new to Unix, and recently I discovered that after I set an environment variable in the shell, it seems to vanish after I run any program.

Here's an example:
```

ceclauson@ceclauson-laptop:~$ env x=100
SSH_AGENT_PID=5574
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
XDG_SESSION_COOKIE=470228213534a906a41875004850a500-1217146737.419856-483254265
GTK_RC_FILES=/etc/gtk/gtkrc:/home/ceclauson/.gtkrc-1.2-gnome2
WINDOWID=52428895
USER=ceclauson
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-RFxsfc5537/agent.5537
GNOME_KEYRING_SOCKET=/tmp/keyring-baQeMv/socket
SESSION_MANAGER=local/ceclauson-laptop:/tmp/.ICE-unix/5537
USERNAME=ceclauson
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/ceclauson
LANG=en_US.UTF-8
GNOME_KEYRING_PID=5534
GDM_LANG=en_US.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/ceclauson
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=ceclauson
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-fyJUSHxl2b,guid=0d49f6e5af2be4530ed45100488c2f73
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/ceclauson/.Xauthority
_=/usr/bin/env
x=100
ceclauson@ceclauson-laptop:~$ echo hello
hello
ceclauson@ceclauson-laptop:~$ env
SSH_AGENT_PID=5574
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
XDG_SESSION_COOKIE=470228213534a906a41875004850a500-1217146737.419856-483254265
GTK_RC_FILES=/etc/gtk/gtkrc:/home/ceclauson/.gtkrc-1.2-gnome2
WINDOWID=52428895
USER=ceclauson
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-RFxsfc5537/agent.5537
GNOME_KEYRING_SOCKET=/tmp/keyring-baQeMv/socket
SESSION_MANAGER=local/ceclauson-laptop:/tmp/.ICE-unix/5537
USERNAME=ceclauson
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/ceclauson
LANG=en_US.UTF-8
GNOME_KEYRING_PID=5534
GDM_LANG=en_US.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/ceclauson
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=ceclauson
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-fyJUSHxl2b,guid=0d49f6e5af2be4530ed45100488c2f73
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/ceclauson/.Xauthority
_=/usr/bin/env
ceclauson@ceclauson-laptop:~$ 

```

As you can see, I can set x to 100, and this shows up in the environment.  But after I run any command (in this case "echo hello"), the environment is reset, and x is no longer defined in the environment.  Is this normal behavior on a Unix system?  If so, how do I make an environment variable more persistent?

Thanks in advance,
Cooper

---

### Post by ajmorris on 2008-07-27
hi there,
when you set an environment through 'export' it only lasts for the life of the bash session. If you want it to stay permanently, add it in the syntax of 'export variable=value' to ~/.bashrc

AJ

---

### Post by dexter.deepak on 2008-07-27
either add this to ~/.bashrc or to ~/.profile
```
export var=value
```

the only advantage .profile gives you is that you can use the global variables even if you have remote logins ..or you use ssh ,etc.

---

### Post by ceclauson on 2008-07-27
Excellent :-)

Thanks so much for your help!

---

