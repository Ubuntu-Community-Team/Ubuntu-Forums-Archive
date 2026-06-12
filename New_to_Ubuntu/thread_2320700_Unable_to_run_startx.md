---
title: "Unable to run startx"
date: 2016-04-16
forum: New to Ubuntu
---

### Post by Copperhorse on 2016-04-16
Can anyone help me access the GUI? First time doing anything with Linux, I have no idea what I'm doing.

login as: root
root@172.106.8.19's password:
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic x86_64)


 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


188 packages can be updated.
102 updates are security updates.


root@localhost:~# startx
hostname: Name or service not known
xauth: (stdin):1:  bad display name "localhost.localdomain:1" in "add" command




X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux localhost.localdomain 3.13.0-24-generic #47-Ubun                                                                                                                                                             tu SMP Fri May 2 23:30:00 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=1c4b4b                                                                                                                                                             7b-5e73-4c87-85b8-cba6e526ede9 ro splash quiet vt.handoff=7
Build Date: 16 April 2014  01:36:29PM
xorg-server 2:1.15.1-0ubuntu2 (For technical support please see [http://www.ubunt](http://www.ubunt)                                                                                                                                                             u.com/support)
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Apr 17 02:43:37 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
setversion 1.4 failed: Permission denied
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
(EE)
Fatal server error:
(EE) Cannot run in framebuffer mode. Please specify busIDs        for all frameb                                                                                                                                                             uffer devices
(EE)
(EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
(EE) Please also check the log file at "/var/log/Xorg.1.log" for additional info                                                                                                                                                             rmation.
(EE)
(EE) Server terminated with error (1). Closing log file.
^Cxinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: unexpected signal 2
xauth: (argv):1:  bad display name "localhost.localdomain:1" in "remove" command

---

### Post by Bashing-om on 2016-04-16
Copperhorse; Oh Boy !

Running 'startx' as root can have and does have BAD bad bad side effects .. "root" now owns "your" /home. Only one of the reasons one does not enable 'root' except as need and as known .

So, let's determine the proper way to start the GUI from terminal.
What Desktop Environment is this ? If a standard ubuntu install, then it is unity. Else, well .. in some (E)nvironments the 'startx' command is valid (xfce4 for 1) - BUT not as 'root !! .
That command in 14.04's unity is:
```

sudo service lightdm start

```

But 1st is to get this system updated; then get your access rights restored to your /home.

At the login screen key combo clt+alt+F1 will yield a console interface.
here execute terminal commands:
```

sudo apt update
sudo apt full-upgrade

```

Now we "look" at your access rights:
post back - Between code tags - the outputs:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[INDENT][INDENT]stepping up on that curve of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Copperhorse on 2016-04-16
> **Bashing-om said:**
> Copperhorse; Oh Boy !

Running 'startx' as root can have and does have BAD bad bad side effects .. "root" now owns "your" /home. Only one of the reasons one does not enable 'root' except as need and as known .

So, let's determine the proper way to start the GUI from terminal.
What Desktop Environment is this ? If a standard ubuntu install, then it is unity. Else, well .. in some (E)nvironments the 'startx' command is valid (xfce4 for 1) - BUT not as 'root !! .
That command in 14.04's unity is:
```

sudo service lightdm start

```

But 1st is to get this system updated; then get your access rights restored to your /home.

At the login screen key combo clt+alt+F1 will yield a console interface.
here execute terminal commands:
```

sudo apt update
sudo apt full-upgrade

```

Now we "look" at your access rights:
post back - Between code tags - the outputs:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT][INDENT]ain't nothing but a thing[INDENT][INDENT]stepping up on that curve of learning
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```
login as: rootroot@172.106.12.77's password:
Welcome to Ubuntu 14.04.4 LTS (GNU/Linux 3.13.0-24-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


*** System restart required ***
root@localhost:~# ls -al .Xauthority
-rw------- 1 root root 0 Apr 16 19:24 .Xauthority
root@localhost:~# ls -al .ICEauthority
ls: cannot access .ICEauthority: No such file or directory
root@localhost:~# ls -al /home
total 8
drwxr-xr-x  2 root root 4096 May  6  2014 .
drwxr-xr-x 23 root root 4096 Apr 16 19:20 ..
root@localhost:~#

```

---

### Post by Bashing-om on 2016-04-16
Copperhorse; Ouch ...

We do not want to work from a 'root' access ... bad bad bad things can happen.
As advised .. log into the system from the login screen .. or advise how you are booting the system to what ?

We want to work as "your" normal user account ... we fix the access rights using 'sudo' to change the access back to 'you' .

From "your" login .. what now ?
```

ls -al .ICEauthority
ls -al /home

```

[INDENT][INDENT]getting a correct perspective on the situation
[/INDENT][/INDENT]

---

### Post by Copperhorse on 2016-04-16
> **Bashing-om said:**
> Copperhorse; Ouch ...

We do not want to work from a 'root' access ... bad bad bad things can happen.
As advised .. log into the system from the login screen .. or advise how you are booting the system to what ?

We want to work as "your" normal user account ... we fix the access rights using 'sudo' to change the access back to 'you' .

From "your" login .. what now ?
```

ls -al .ICEauthority
ls -al /home

```
[INDENT][INDENT]getting a correct perspective on the situation
[/INDENT]
[/INDENT]


As far as I know I don't have a normal account. I would have to create one using root, which I have no idea how to do. I'm connecting using PuTTY.

---

### Post by Bashing-om on 2016-04-16
Copperhorse; Yuk ...

So this install is a server edition ? And ....

did you add a GUI on top ?

Be aware, that I have absolutely no experience with putty ( Windows ??) .. I may not be much more use to you.
Why not 'root' :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[INDENT][INDENT]I do keep try'n
[/INDENT][/INDENT]

---

### Post by Copperhorse on 2016-04-16
> **Bashing-om said:**
> Copperhorse; Yuk ...

So this install is a server edition ? And ....

did you add a GUI on top ?

Be aware, that I have absolutely no experience with putty ( Windows ??) .. I may not be much more use to you.
Why not 'root' :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[INDENT][INDENT]I do keep try'n
[/INDENT]
[/INDENT]


I believe it is a server edition. What I'm trying to do is get a GUI running so I can use it, because I have no idea how to run it through command prompt. However whenever I try doing anything I find online I always get errors.

---

### Post by grahammechanical on 2016-04-16
When we install Ubuntu we are asked to provide a user name and password. That creates a normal or standard user account but with Administrator access when needed. Therefore, we log in with our user password and then when we need to run a command with administrator privileges we prefix the command with the term "sudo" but without the quotes.

Also, while we are working at the desktop if we try to do something that requires administrator privileges a dialog will appear that will ask us to authentic the action. And it is our user password that allows us to authenticate and in that one instant we become the administrator or root user as it would be called in some other Linux distributions.

Because of the damage that a root user can do even when the user is experienced let alone by someone who has no idea what they are doing, in Ubuntu the root user account is disabled by default & we avoid working as root.

What happens when you load Ubuntu? We assume that it does not load to a login screen? Correct?

Regards

---

### Post by Copperhorse on 2016-04-16
> **grahammechanical said:**
> When we install Ubuntu we are asked to provide a user name and password. That creates a normal or standard user account but with Administrator access when needed. Therefore, we log in with our user password and then when we need to run a command with administrator privileges we prefix the command with the term "sudo" but without the quotes.

Also, while we are working at the desktop if we try to do something that requires administrator privileges a dialog will appear that will ask us to authentic the action. And it is our user password that allows us to authenticate and in that one instant we become the administrator or root user as it would be called in some other Linux distributions.

Because of the damage that a root user can do even when the user is experienced let alone by someone who has no idea what they are doing, in Ubuntu the root user account is disabled by default & we avoid working as root.

What happens when you load Ubuntu? We assume that it does not load to a login screen? Correct?

Regards

[IMG]https://i.gyazo.com/e17496a3cd5d3896d176ac98129b824f.png[/IMG]
[IMG]https://i.gyazo.com/4068b5ea4e584de61537aeb1c87f2bc7.png[/IMG]
[IMG]https://i.gyazo.com/5c509a4767af0f57f4eec778e88781bb.png[/IMG]
[IMG]https://i.gyazo.com/50132348bc8340a788b7cd81063f2c67.png[/IMG]

---

### Post by Bashing-om on 2016-04-16
Copperhorse; Uh Huh ...

So ... as a server .. are you aware there is no GUI in the default install ??
I am trying to put myself in your shoes and see what there is to to this system and the access .

This ain't no standard 14.04 desktop install, ANd not setting at the terminal.

[INDENT][INDENT]done so much, for so long, with so little
[INDENT][INDENT]qualified to do anything
[INDENT][INDENT][INDENT]with nothing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Copperhorse on 2016-04-16
> **Bashing-om said:**
> Copperhorse; Uh Huh ...

So ... as a server .. are you aware there is no GUI in the default install ??
I am trying to put myself in your shoes and see what there is to to this system and the access .

This ain't no standard 14.04 desktop install, ANd not setting at the terminal.
[INDENT][INDENT]done so much, for so long, with so little[INDENT][INDENT]qualified to do anything[INDENT][INDENT][INDENT]with nothing
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Yes I am aware now, that's why I'm trying to manually get a GUI going.

---

### Post by Bashing-om on 2016-04-16
Copperhorse; K

> 
Yes I am aware now, that's why I'm trying to manually get a GUI going.


So, where are you in that process ? What DE have you decided on ?

[INDENT][INDENT]apt to the rescue 
[/INDENT][/INDENT]

---

### Post by Copperhorse on 2016-04-16
> **Bashing-om said:**
> Copperhorse; K



So, where are you in that process ? What DE have you decided on ?
[INDENT][INDENT]apt to the rescue 
[/INDENT]
[/INDENT]


I wish to use KDE.

---

### Post by Bashing-om on 2016-04-16
Copperhorse; Welp ...

Have not seen kde since release 9.04; not much I can help with directly.
See if this helps:
[http://help.ubuntu.com/community/InstallingKDE](http://help.ubuntu.com/community/InstallingKDE)

[INDENT][INDENT]what a web we weave for our selves
[/INDENT][/INDENT]

---

### Post by oldos2er on 2016-04-16
Do you have access to another computer where you can download an Ubuntu desktop ISO and create a bootable USB or DVD? I don't understand why you wanted the server version if you're new to Ubuntu and Linux.

---

