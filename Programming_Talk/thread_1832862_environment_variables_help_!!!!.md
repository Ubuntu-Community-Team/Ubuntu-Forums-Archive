---
title: "environment variables help !!!!"
date: 2011-08-25
forum: Programming Talk
---

### Post by ankit3111 on 2011-08-25
#include<stdio.h>
#include<dirent.h>

void main(int argc,char *argv[],char *envp[])
{
	chdir("/home/ankit");
	while(*(envp++)!=NULL)
		printf("%s\n",*envp);
}


output:-

SSH_AGENT_PID=1238
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=936d34cd44fe40c252f91e0f00000006-1314185014.407072-552099930
WINDOWID=46137381
GNOME_KEYRING_CONTROL=/tmp/keyring-MR9CNe
GTK_MODULES=canberra-gtk-module
USER=ankit
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-MR9CNe/ssh
SESSION_MANAGER=local/ankit-desktop:@/tmp/.ICE-unix/1205,unix/ankit-desktop:/tmp/.ICE-unix/1205
USERNAME=ankit
DEFAULTS_PATH=/usr/share/gconf/gnome-classic.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-classic:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=gnome-classic
LC_MESSAGES=en_IN.UTF-8
PWD=/home/ankit/cres
GDM_KEYBOARD_LAYOUT=us
LANG=en_IN
GDM_LANG=en_IN
MANDATORY_PATH=/usr/share/gconf/gnome-classic.mandatory.path
UBUNTU_MENUPROXY=libappmenu.so
GDMSESSION=gnome-classic
SHLVL=1
HOME=/home/ankit
LANGUAGE=en_IN:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=ankit
XDG_DATA_DIRS=/usr/share/gnome-classic:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Qf8EELdnPx,guid=226b8a0f2e926ad4e02e2c7100000012
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-ankit-zN5MTp/database
OLDPWD=/home/ankit
_=./183
Segmentation fault






Why do i get a segmentation fault at the end ??
please help .

---

### Post by dwhitney67 on 2011-08-25
You really would be best served incrementing the envp pointer after you have printed it's current value:
```

#include <stdio.h>

int main(int argc, char *argv[], char *envp[])
{
   while (*envp != NULL)
      printf("%s\n", *envp++);
   return 0;
}

```
I'm not sure why you have a call to chdir(), or even why you included dirent.h.  The code above should work.

And as for your seg fault, it is quite possible because *envp was pointing to NULL after you had incremented it.  This is what you had:

1.  Compare contents of envp with NULL
2.  Increment envp
3.  Print contents of envp... Oops!  envp could be pointing to NULL now!

P.S. On my system, printf() prints the string "null" with your original code; in other words, it does not segfault.

---

### Post by Bachstelze on 2011-08-25
> **dwhitney67 said:**
> 
P.S. On my system, printf() prints the string "null" with your original code; in other words, it does not segfault.

This probably shouldn't be relied on. The standard doesn't say anything about what happens for %s conversions if the pointer is NULL. There is a major algorithmic flaw here that shouldn't be minimized.

---

