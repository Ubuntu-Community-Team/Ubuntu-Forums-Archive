---
title: "Setting Root Java_Home"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jadionne on 2008-05-26
I am trying to run a Java based dashbord on Ubuntu.  I believe I am running the latest version 8.something.  I also dont believe that the version I am running matters this time.

I have set the java_home env variable for my userid, I can see it when I use the env command.  

The thing is I have to start the application in "root mode" with sudo.  When I execute sudo env i do not see the java_home dir set.

The application complains as well that it is not set.

How do I set the Java_home env variable for the root user when the root user is disabled?

---

### Post by ibutho on 2008-05-26
You could set the variable in a global file e.g. in /etc/environment. This enables the variable for all users on the system.

---

### Post by jadionne on 2008-05-26
> **ibutho said:**
> You could set the variable in a global file e.g. in /etc/environment. This enables the variable for all users on the system.

is there a special name for this global file?  What do I name it?

---

### Post by jadionne on 2008-05-26
> **jadionne said:**
> is there a special name for this global file?  What do I name it?

Ahhh i get it.  the file name is environment.  I did that and I got the same result.  Do I need to log off and then back on?

also when i have more time I will post the contents of the environment file, the output of my env command, and the error that I am getting

---

### Post by ibutho on 2008-05-26
Yes, you need to logout and back in again.

---

### Post by Nepherte on 2008-05-26
A better option is to put an export command at the end of your .bashrc file. That way you don't have to edit root owned files and the change only takes place for your user.

```
gedit ~/.bashrc
```
and add the following to the end of the file:
```
export JAVA_HOME='pathtojava'
```

---

### Post by jadionne on 2008-05-26
> **Nepherte said:**
> A better option is to put an export command at the end of your .bashrc file. That way you don't have to edit root owned files and the change only takes place for your user.

```
gedit ~/.bashrc
```
and add the following to the end of the file:
```
export JAVA_HOME='pathtojava'
```


I have already done this, as well as added the export command to my .profile file.  This does not seem to affect the user id when I use the sudo command though.

---

### Post by jadionne on 2008-05-27
Ok here is the output from a few commands that may shed some light

ENV comand:
```

jadionne@jadionne-desktop:~/dash/bin$ env
GPG_AGENT_INFO=/tmp/seahorse-7xo8Y7/S.gpg-agent:5860:1
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
XDG_SESSION_COOKIE=4a9decab6aba587fb315090047f3c628-1211853423.452211-1827449756
GTK_RC_FILES=/etc/gtk/gtkrc:/home/jadionne/.gtkrc-1.2-gnome2
WINDOWID=41943132
USER=jadionne
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SSH_AUTH_SOCK=/tmp/keyring-X4n8jD/ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-X4n8jD/socket
SESSION_MANAGER=local/jadionne-desktop:/tmp/.ICE-unix/5744
USERNAME=jadionne
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=gnome
GDM_XSERVER_LOCATION=local
PWD=/home/jadionne/dash/bin
JAVA_HOME=/usr/lib/jvm/java-6-sun
LANG=en_US.UTF-8
GNOME_KEYRING_PID=5743
GDM_LANG=en_US.UTF-8
GDMSESSION=gnome
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/jadionne
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=jadionne
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Gyz7rPD2FN,guid=42fa6fc1ff80decb3b38b169483b6a71
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/jadionne/.Xauthority
_=/usr/bin/env
OLDPWD=/home/jadionne/dash

```


SUDO ENV Comand
```

jadionne@jadionne-desktop:~/dash/bin$ sudo env
[sudo] password for jadionne: 
TERM=xterm
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
LANG=en_US.UTF-8
HOME=/home/jadionne
DISPLAY=:0.0
COLORTERM=gnome-terminal
XAUTHORITY=/home/jadionne/.Xauthority
SHELL=/bin/bash
LOGNAME=root
USER=root
USERNAME=root
SUDO_COMMAND=/usr/bin/env
SUDO_USER=jadionne
SUDO_UID=1000
SUDO_GID=0

```

Output from trying to start APP:
```

jadionne@jadionne-desktop:~/dash/bin$ sudo ./catalina.sh start
[sudo] password for jadionne: 
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

Now I am a total nube with Linux and Ubuntu, but the output from the env says i have Java_home set, but it is not listed in the sudo env command.  I have added the export line to the .bashrc file for the root user and my user id.  I also added it to the .profile files for both users just fore giggles.  I am out of ideas, any thoughts?

Maybe I have the wrong java...is there a diff between what I have loaded and the java sdk?

---

### Post by jadionne on 2008-05-27
There is so much activity on this forum how do any of the new post get answered or even seen?

---

### Post by jadionne on 2008-05-28
I fixed this problem by activating the root account, switching to the root account in my terminal window, and activated the application.  

This worked but I dont like it.  I think that the root account was locked for a reason.  How can I get the java_home env variable set for the root user and activate it using sudo and not logging is as root?

---

### Post by rfields on 2008-12-09
Sorry this reply is coming many months after you posted.  I was just trying to solve this problem today and I came across this thread during my search for answers.  I found the solution elsewhere and am including it here for the benefit of anyone else who searches for something like "sudo JAVA_HOME env".

sudo uses a blacklist/whitelist system for environment variables.  With recent Ubuntu versions (or maybe all versions), sudo is using the whitelist mode (which is done by having the line "Defaults     env_reset" in the /etc/sudoers file.  This whitelist mode is a good thing, so don't disable it.

The solution is as follows:

First, go ahead and add JAVA_HOME to the /etc/environment file as instructed in a previous reply.

Second, run "sudo visudo" to edit your /etc/sudoers file.  Add the line "Defaults env_keep+=JAVA_HOME" somewhere in the file.  I have it right under the "Defaults env_reset" line.

Now, run "sudo env" and you should see JAVA_HOME listed.  You may have to log out and back in first, but I wouldn't think so.

NOTE: If you're not familiar with the vi editor, you may run into trouble with that second step.  I'm not sure if there's a way to specify an editor like pico to use in place of visudo...  Hopefully someone else can jump in and provide instructions for changing /etc/sudoers without using visudo.

---

### Post by jrbromberg on 2009-03-11
Thank you rfields!!

---

### Post by sg552sg552 on 2011-02-27
Thank you very much, rfields!!! You saved my life!!!!!   

Great job!

---

