---
title: "Cups not running"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Beerboy on 2008-11-04
Hi

I've just upgraded from 8.04 to 8.10 and have a problem. On bootup there is no access to printing. If I check in System/Admin/Printing, there are no printers shown and message at bottom of box says not connected. If I select help in the printer config box and troubleshoot it says spooler / scheduler not running. If I go to System/Admin/Services there is no CUPS or similar printing service to run at boot time.

However if I type sudo cupsd or /etc/init.d/cups.dpkg-new start in terminal everything works and I have my 2 network printers and PDF back in the printer config box. Seems like I have what is needed but somehow the config files are screwed up. Whilst upgrading I think it asked if I wanted to keep some config files or replace and I maybe stupidly chose replace. Any help welcomed.
Thanks

Beerboy

---

### Post by cmnorton on 2008-11-04
Go to an X-term (command line), and enter this command:

ps -ef | grep cups

You should see this. (I'm running Ubuntu 8.04).

root      5564     1  0 08:10 ?        00:00:08 /usr/sbin/cupsd

This sounds like your cups and other config files were saved off and then overwritten during your upgrade. You could go look in /etc/cups.

You can also always enter this at the command line:

sudo apt-get install cupsys

and see what output you get from that.

---

### Post by mindwarp on 2008-11-04
I would do the following:

**sudo mv /etc/init.d/cups.dpkg-new /etc/init.d/cups**

And check under **System->Administration->Services** and make sure cups is enabled.

You can find config files that may be messed up by running:

**find /etc/ -name "*.dpkg-new"**

---

### Post by Beerboy on 2008-11-04
Thanks for reply. 

I tried sudo mv /etc/init.d/cups.dpkg-new /etc/init.d/cups but service not listed under System/Admin/Services  

I tried apt-get install cups with following output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version.
The following packages were automatically installed and are no longer required:
  libpythonize0 libqt4-core pykdeextensions libqt4-gui libpoppler-qt2
  python-kde3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 70 not upgraded.
I used cups as I gather this has replaced cupsys in 8.10

Seems that I have the latest version.

Running the following command gives - 
 ~$ ps -ef | grep cups
root      6638     1  0 22:10 ?        00:00:00 cupsd
geoff     7185  7102  0 22:28 pts/0    00:00:00 grep cups

not sure what this means.

Any other suggestions

Thanks

---

### Post by cmnorton on 2008-11-05
The cups daemon is running.

Try configuring a printer locally, even if that is not your final goal, using localhost:631. You can also try configuring through the Admin panel. I prefer CUPS' web interface.

---

### Post by Beerboy on 2008-11-07
Hi

Apologies to cmnorton, but when I entered the command ps -ef | grep cups this was after I had entered sudo cupsd subsequent to bootup. If I enter the same command prior to cupsd, then I get the following output:

14847 pts/0    S+     0:00  \_ grep cups ORBIT_SOCKETDIR=/tmp/orbit-geoff GPG_AGENT_INFO=/tmp/seahorse-b5DW97/S.gpg-agent:8072:1 SHELL=/bin/bash TERM=xterm XDG_SESSION_COOKIE=7ece3a9769eea55a76b0d10047af6547-1226076825.497811-1280365447 GTK_RC_FILES=/etc/gtk/gtkrc:/home/geoff/.gtkrc-1.2-gnome2 WINDOWID=46137404 USER=geoff LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36: SSH_AUTH_SOCK=/tmp/keyring-eLA2GG/ssh GNOME_KEYRING_SOCKET=/tmp/keyring-eLA2GG/socket SESSION_MANAGER=local/geoff-desktop:/tmp/.ICE-unix/7994 USERNAME=geoff PATH=/home/geoff/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games DESKTOP_SESSION=gnome GDM_XSERVER_LOCATION=local PWD=/home/geoff LANG=en_GB.UTF-8 GNOME_KEYRING_PID=7984 GDM_LANG=en_GB.UTF-8 GDMSESSION=gnome HISTCONTROL=ignoreboth SHLVL=1 HOME=/home/geoff GNOME_DESKTOP_SESSION_ID=this-is-deprecated LOGNAME=geoff XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/ DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-0ZMcf0teiA,guid=977a1962652942edeebd11a34914729a LESSOPEN=| /usr/bin/lesspipe %s WINDOWPATH=7 DISPLAY=:0.0 LESSCLOSE=/usr/bin/lesspipe %s %s COLORTERM=gnome-terminal XAUTHORITY=/tmp/.gdmAWO8JU _=/bin/grep

Does this provide any clues?

Thanks

---

### Post by cmnorton on 2008-11-29
> **Beerboy said:**
> Hi

Apologies to cmnorton, but when I entered the command ps -ef | grep cups this was after I had entered sudo cupsd subsequent to bootup. If I enter the same command prior to cupsd, then I get the following output:

14847 pts/0    S+     0:00  \_ grep cups ORBIT_SOCKETDIR=/tmp/orbit-geoff GPG_AGENT_INFO=/tmp/seahorse-b5DW97/S.gpg-agent:8072:1 SHELL=/bin/bash TERM=xterm XDG_SESSION_COOKIE=7ece3a9769eea55a76b0d10047af6547-1226076825.497811-1280365447 GTK_RC_FILES=/etc/gtk/gtkrc:/home/geoff/.gtkrc-1.2-gnome2 WINDOWID=46137404 USER=geoff LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36: SSH_AUTH_SOCK=/tmp/keyring-eLA2GG/ssh GNOME_KEYRING_SOCKET=/tmp/keyring-eLA2GG/socket SESSION_MANAGER=local/geoff-desktop:/tmp/.ICE-unix/7994 USERNAME=geoff PATH=/home/geoff/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games DESKTOP_SESSION=gnome GDM_XSERVER_LOCATION=local PWD=/home/geoff LANG=en_GB.UTF-8 GNOME_KEYRING_PID=7984 GDM_LANG=en_GB.UTF-8 GDMSESSION=gnome HISTCONTROL=ignoreboth SHLVL=1 HOME=/home/geoff GNOME_DESKTOP_SESSION_ID=this-is-deprecated LOGNAME=geoff XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/ DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-0ZMcf0teiA,guid=977a1962652942edeebd11a34914729a LESSOPEN=| /usr/bin/lesspipe %s WINDOWPATH=7 DISPLAY=:0.0 LESSCLOSE=/usr/bin/lesspipe %s %s COLORTERM=gnome-terminal XAUTHORITY=/tmp/.gdmAWO8JU _=/bin/grep

Does this provide any clues?

Thanks

You would enter sudo /etc/init.d/cups start.

I believe it's cups and not cupsd. This service should be configured under Admin/services.

---

