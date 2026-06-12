---
title: "Why arm-linux-g++ cannot be found"
date: 2012-08-06
forum: Programming Talk
---

### Post by pellyhawk on 2012-08-06
I am debugging a project and meet the following issue:

```
mike@mike-desktop:/mnt/hgfs/VBox_Shared/dc$ make
make target -C commonLib_1
make[1]: Entering directory `/mnt/hgfs/VBox_Shared/dc/commonLib_1'
arm-linux-g++ -O2 -fPIC -shared -o libshm_event.so shm_event.cpp
cp ./libshm_event.so /lib/
[COLOR="Red"]cp: cannot create regular file `/lib/libshm_event.so': Permission denied[/COLOR]
make[1]: *** [libshm_event.so] Error 1
make[1]: Leaving directory `/mnt/hgfs/VBox_Shared/dc/commonLib_1'
make: *** [subdir] Error 2

```

I found:

```
drwxr-xr-x  20 root root 12288 2012-06-11 01:11 lib/

```

So I type "sudo make" and got:
```
mike@mike-desktop:/mnt/hgfs/VBox_Shared/dc$ sudo make
[sudo] password for mike: 
make target -C commonLib_1
make[1]: Entering directory `/mnt/hgfs/VBox_Shared/dc/commonLib_1'
arm-linux-g++ -O2 -fPIC -shared -o libshm_his.so shm_his.cpp
[COLOR="Red"]make[1]: arm-linux-g++: Command not found[/COLOR]
make[1]: *** [libshm_his.so] Error 127
make[1]: Leaving directory `/mnt/hgfs/VBox_Shared/dc/commonLib_1'
make: *** [subdir] Error 2
mike@mike-desktop:/mnt/hgfs/VBox_Shared/dc$ 
```

Why "sudo make" got these result?

```
mike@mike-desktop:/mnt/hgfs/VBox_Shared/dc$ which arm-linux-g++
/usr/local/arm/3.4.1/bin/arm-linux-g++
mike@mike-desktop:/mnt/hgfs/VBox_Shared/dc$ echo $PATH
/usr/local/arm/3.4.1/bin:/usr/local/Trolltech/Qt-4.7.3-static/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mike/CodeSourcery/Sourcery_G++_Lite/bin

```

Thanks.

---

### Post by Bachstelze on 2012-08-06
Your Makefile is wrong. Normally, make should compile only, not install. Here it seems it's doing both.

That said, your problem is that arm-linux-g++ is in your PATH, but not in root's, so you should login as root with

```
sudo -i
```

and modify .profile in root's home directory (/root).

---

### Post by pellyhawk on 2012-08-06
> **Bachstelze said:**
> Your Makefile is wrong. Normally, make should compile only, not install. Here it seems it's doing both.


How do you find out my Makefile run installation? Would you please point it out for me?

> That said, your problem is that arm-linux-g++ is in your PATH, but not in root's, so you should login as root with

```
sudo -i
```

and modify .profile in root's home directory (/root).

But /etc/profile is read once logging in and I have put PATH environment variable in it.

---

### Post by trent.josephsen on 2012-08-06
> **pellyhawk said:**
> How do you find out my Makefile run installation? Would you please point it out for me?

That's easy -- it's trying to create a file in /lib. Compilation should rarely if ever create files anywhere except the build tree or /tmp.

---

### Post by Bachstelze on 2012-08-06
> **pellyhawk said:**
> 
But /etc/profile is read once logging in and I have put PATH environment variable in it.

Sorry, my bad. You shouldn't add it to .profle but to .bashrc (or the equivalent for your shell). This is because .profile is parsed only when the shell is run as a login shell, which is not the case when you run a command with sudo.

---

### Post by pellyhawk on 2012-08-06
> That's easy -- it's trying to create a file in /lib. Compilation should rarely [COLOR="Red"]if ever create files anywhere except the build tree or /tmp[/COLOR].

What do you mean? sorry, I only understand I created a file, which is rarely done by Compilation.

> Sorry, my bad. You shouldn't add it to .profle but to .bashrc (or the equivalent for your shell). This is because .profile is parsed only when the shell is run as a login shell, which is not the case when you run a command with sudo.

I was confused. Well, you know, /etc/profile is read while any user logging in and ~/.profile is read while the user equivalent to it logging in.

So if add "export PATH=/usr/local/arm/3.4.1/bin:$PATH" at the bottom of /etc/profile, any user logging in will find arm-linux-g++. And you can see the "echo $PATH"result I put it in the original post. Why it cannot find out arm-linux-g++? I think "make" and "sudo make" should both find it smoothly. But it is no so:confused: And building a project by logging as root sounds very unusually.

By the way, "sudo -i" can make user transform to root. How can I transform to another user from one user? I type "man sudo" and cannot find any answer.

---

### Post by Bachstelze on 2012-08-06
> **pellyhawk said:**
> 
I was confused. Well, you know, /etc/profile is read while any user logging in and ~/.profile is read while the user equivalent to it logging in.

So if add "export PATH=/usr/local/arm/3.4.1/bin:$PATH" at the bottom of /etc/profile, any user logging in will find arm-linux-g++. And you can see the "echo $PATH"result I put it in the original post. Why it cannot find out arm-linux-g++? I think "make" and "sudo make" should both find it smoothly. But it is no so:confused: And building a project by logging as root sounds very unusually.

Running a command with sudo is *not* equivalent to logging in. (Running [font=monospace]sudo -i[/font] is.)

```
firas@itsuki ~ % sudo cat /root/.profile
[sudo] password for firas: 
# ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
  if [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
fi
export PATH=$PATH:/foo

mesg n
firas@itsuki ~ % sudo env
HOME=/home/firas
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
TERM=xterm-color
LANG=en_GB.UTF-8
LC_ALL=en_GB.UTF-8
TZ=/usr/share/zoneinfo/Europe/Paris
SHELL=/usr/bin/zsh
LOGNAME=root
USER=root
USERNAME=root
MAIL=/var/mail/root
SUDO_COMMAND=/usr/bin/env
SUDO_USER=firas
SUDO_UID=1000
SUDO_GID=1000
firas@itsuki ~ % sudo -i
root@itsuki:~# env
SHELL=/bin/bash
TERM=xterm-color
LC_ALL=en_GB.UTF-8
USER=root
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SUDO_USER=firas
SUDO_UID=1000
USERNAME=root
MAIL=/var/mail/root
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/foo
PWD=/root
LANG=en_GB.UTF-8
TZ=/usr/share/zoneinfo/Europe/Paris
SHLVL=1
SUDO_COMMAND=/bin/bash
HOME=/root
LOGNAME=root
LESSOPEN=| /usr/bin/lesspipe %s
SUDO_GID=1000
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

```

Notice that in the first case, /foo is not appended to PATH, but in the second case it is.

> By the way, "sudo -i" can make user transform to root. How can I transform to another user from one user? I type "man sudo" and cannot find any answer.

Look at the [font=monospace]-u[/font] flag.

---

### Post by pellyhawk on 2012-08-06
> **Bachstelze said:**
> 
Notice that in the first case, /foo is not appended to PATH, but in the second case it is.


But, arm-linux-g++ is not in /foo directory. appending /foo seems useless for me to find arm-linux-g++.

---

### Post by Bachstelze on 2012-08-06
-_-

The same is true with any other directory, of course...

---

### Post by pellyhawk on 2012-08-06
I add "export PATH=/usr/local/arm/3.4.1/bin:$PATH" at the bottom of /etc/profile(not ~/.profile) and got:

```
mike@mike-desktop:~$ [COLOR="Red"]echo $PATH[/COLOR]
[COLOR="Red"]/usr/local/arm/3.4.1/bin[/COLOR]:/usr/local/Trolltech/Qt-4.7.3-static/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mike/CodeSourcery/Sourcery_G++_Lite/bin
mike@mike-desktop:~$ 
mike@mike-desktop:~$ [COLOR="Red"]sudo echo $PATH[/COLOR]
[sudo] password for mike: 
[COLOR="Red"]/usr/local/arm/3.4.1/bin[/COLOR]:/usr/local/Trolltech/Qt-4.7.3-static/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mike/CodeSourcery/Sourcery_G++_Lite/bin
mike@mike-desktop:~$ 

```

I did not modify ~/.profile, but I guess I will get the similar result. (If so, there will be no need to modify /etc/bash.bashrc or ~/.bashrc.) Why arm-linux-g++ still cannot be find?

PS: I type "man sudo" and find "sudo -i" and "sudo -s" are very similar, the difference between them is "sudo -i" will read resource file such as .profile?? But neither of them mentioned  the user will be relogin as root. Especially, passwd(5) means??

Thanks

---

### Post by Bachstelze on 2012-08-07
When you do

```
sudo echo $PATH
```

it outputs *your* PATH, not root's. I told you several times that you need to modify bashrc, not profile. Why are you asking a question if you ignore the answers you are given?

---

### Post by pellyhawk on 2012-08-07
> **Bachstelze said:**
> When you do

```
sudo echo $PATH
```

it outputs *your* PATH, not root's. I told you several times that you need to modify bashrc, not profile. Why are you asking a question if you ignore the answers you are given?

Sorry, at first I was totally confused. I thought profile and bashrc will both be read. But thank you for your patience, and now I begin to be clear: profile will be read only when logining in, while bashrc will be read when opening a bash shell.

Can I summarize all the results? And I wonder whether my summary is right.

a)If run "sudo -i" and "make" user has transform root
Modifying profile or bashrc will both be OK. Because profile and bashrc will both be read.
b)If run "sudo make"
Only modifying bashrc will be OK. Because profile will not be read. Thus arm-linux-g++ will not be found.

By the way, may I ask 2 more questions? 
1)After running "sudo make", how can I get the value of $PATH since at that time "echo $PATH" cannot output root's?
2)If I do not modify any resource file such as profile or bashrc, which file determine $PATH? 

Thanks a lot.

---

### Post by Bachstelze on 2012-08-07
> **pellyhawk said:**
> Sorry, at first I was totally confused. I thought profile and bashrc will both be read. But thank you for your patience, and now I begin to be clear: profile will be read only when logining in, while bashrc will be read when opening a bash shell.

Can I summarize all the results? And I wonder whether my summary is right.

a)If run "sudo -i" and "make" user has transform root
Modifying profile or bashrc will both be OK. Because profile and bashrc will both be read.
b)If run "sudo make"
Only modifying bashrc will be OK. Because profile will not be read. Thus arm-linux-g++ will not be found.

Right.

> By the way, may I ask 2 more questions? 
1)After running "sudo make", how can I get the value of $PATH since at that time "echo $PATH" cannot output root's?

You can do [font=monospace]sudo env[/font], as I did above.

> 2)If I do not modify any resource file such as profile or bashrc, which file determine $PATH? 

It depends on the OS. In Debian/Ubuntu, it's in /etc/environment.

---

