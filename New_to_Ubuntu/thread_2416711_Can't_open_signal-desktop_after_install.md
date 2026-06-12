---
title: "Can't open signal-desktop after install"
date: 2019-04-13
forum: New to Ubuntu
---

### Post by ashley-c on 2019-04-13
Hello! Newbie here. I've installed signal-desktop and tried to open it. It turned out like this:
```
:~$ signal-desktop

(signal-desktop:764): Gtk-WARNING **: 09:00:04.036: cannot open display:
```
Then I tried:
```
:~$ xhost +localhost
xhost:  unable to open display ""
:~$ xhost +SI:localuser:root
xhost:  unable to open display ""
```

What else can I do to make the program run?
Thank you very much in advance!!

---

### Post by again? on 2019-04-14
Are you running a graphical session (a windowed environment)?
Starts up here Xubuntu 18.04.
```

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] lsb_release -d**
Description:	Ubuntu 18.04.2 LTS

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] loginctl show-session "$XDG_SESSION_ID" -p Type -p Desktop -p Display**
Display=:0
Desktop=xubuntu
Type=x11
```


What's your output for...
```
lsb_release -d
loginctl show-session "$XDG_SESSION_ID" -p Type -p Desktop -p Display

```

---

### Post by ashley-c on 2019-04-15
Thank you for replying!! 
Sorry I'm too new to understand -- what is "graphical session"? Is that possible to update me on this real quick?

And after I input these commands this is what I get:
```
Failed to create bus connection: No such file or directory
```
Do you know why this happens?

---

### Post by again? on 2019-04-15
A graphical session is where you have application windows as opposed to purely working in terminal as you would when connecting via ssh or working in a [tty]("https://askubuntu.com/questions/66195/what-is-a-tty-and-how-do-i-access-a-tty").
A graphical session is the normal default session.
How are you opening a terminal?

If you're getting those sort of errors it's probably time to inform what Ubuntu release and desktop you are using.
What is your terminal output for...
```
lsb_release -a
env
```

---

### Post by ashley-c on 2019-04-15
I'm Windows 10 user and trying to learn how to use Linux. Now I open Ubuntu terminal in Windows start menu (I know it's way too amateur!!)

```
ashley@LAPTOP-MUGMR4IL:~$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
ashley@LAPTOP-MUGMR4IL:~$ env
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
HOSTTYPE=x86_64
LESSCLOSE=/usr/bin/lesspipe %s %s
LANG=C.UTF-8
USER=ashley
PWD=/home/ashley
HOME=/home/ashley
NAME=LAPTOP-MUGMR4IL
XDG_DATA_DIRS=/usr/local/share:/usr/share:/var/lib/snapd/desktop
SHELL=/bin/bash
TERM=xterm-256color
SHLVL=1
LOGNAME=ashley
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/mnt/c/Program Files/WindowsApps/CanonicalGroupLimited.UbuntuonWindows_1804.2018.817.0_x64__79rhkp1fndgsc:/mnt/c/Program Files (x86)/Intel/Intel(R) Management Engine Components/iCLS:/mnt/c/Program Files/Intel/Intel(R) Management Engine Components/iCLS:/mnt/c/Windows/System32:/mnt/c/Windows:/mnt/c/Windows/System32/wbem:/mnt/c/Windows/System32/WindowsPowerShell/v1.0:/mnt/c/Program Files (x86)/Intel/Intel(R) Management Engine Components/DAL:/mnt/c/Program Files/Intel/Intel(R) Management Engine Components/DAL:/mnt/c/Program Files (x86)/Intel/Intel(R) Management Engine Components/IPT:/mnt/c/Program Files/Intel/Intel(R) Management Engine Components/IPT:/mnt/c/Program Files (x86)/PharosSystems/Core:/mnt/c/Windows/System32/OpenSSH:/mnt/e/Python3/Scripts:/mnt/e/Python3:/mnt/c/Users/bjxin/AppData/Local/Microsoft/WindowsApps:/snap/bin
LESSOPEN=| /usr/bin/lesspipe %s
_=/usr/bin/env
OLDPWD=/home/ashley/learn
```

---

### Post by again? on 2019-04-15
Linux on Windows isn't a full Linux install.
You can't run graphical applications... just some linux commands.
signal-desktop is a graphical application which will run in a full Linux install.
[ATTACH=CONFIG]283032[/ATTACH]


[https://askubuntu.com/questions/993225/whats-the-easiest-way-to-run-gui-apps-on-windows-subsystem-for-linux-as-of-2018](https://askubuntu.com/questions/993225/whats-the-easiest-way-to-run-gui-apps-on-windows-subsystem-for-linux-as-of-2018)
See the second answer in above link for an answer, but I would just install a Linux distro in [virtualbox]("https://www.virtualbox.org/wiki").

[URL="https://www.youtube.com/watch?v=QbmRXJJKsvs"]Youtube: How to Install Ubuntu 18.04 LTS on VirtualBox in Windows 10 / Windows 8
[/URL]

---

### Post by Holger_Gehrke on 2019-04-15
Am I right to think you're using Ubuntu inside Windows 10 through the Windows Subsystem for Linux ? If that's so, than this [article]("https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/") might be of some help (basically: WSL is meant for developers who want to use the Linux command line on Windows, to use graphical Linux applications you need to install an X-Server on Windows).

Holger

---

### Post by ashley-c on 2019-04-15
I see. You've been very helpful! Thank you so much! :KS

---

