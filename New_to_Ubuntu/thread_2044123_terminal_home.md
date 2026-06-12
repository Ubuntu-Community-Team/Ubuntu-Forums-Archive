---
title: "terminal home"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by covername on 2012-08-18
I am trying to run an install file from terminal that is located in home/username/xyz

I can do cd /home/username just find and ls the directory to make sure what i see in the GUI is true but when I /home/username/xyz it always returns invalid directory. I have tried several noob iterations of that and no luck. I was wondering if I could be pointed in the correct direction.



-CV

---

### Post by papibe on 2012-08-18
Hi covername. Welcome to the forums ):P

Using the right click on the terminal you can copy paste what you see there.

Could you post the result of this command?
```
ls ~/
```
Regards.

---

### Post by covername on 2012-08-18
eric@PowerEdge-1750-1:~$ ls ~/
Desktop                                 Pictures
Documents                           Public
Downloads                          TeamSpeak3-Client-linux_x86
examples.desktop     TeamSpeak3-Client-linux_x86-3.0.8.1.run
fancon.sh                              teamspeak3-server_linux-x86
lm_sensors-3.3.2          Templates
Music                                         Videos


none of those can be accessed the way i mentioned above

---

### Post by papibe on 2012-08-18
Let's say you want to run 'TeamSpeak3-Client-linux_x86-3.0.8.1.run'

Either this:
```
./TeamSpeak3-Client-linux_x86-3.0.8.1.run
```
or this:
```
sh TeamSpeak3-Client-linux_x86-3.0.8.1.run
```
Let us know how it goes.
Regards.

---

### Post by covername on 2012-08-18
eric@PowerEdge-1750-1:~$ ./TeamSpeak3-Client-linux_x86-3.0.8.1.run
bash: ./TeamSpeak3-Client-linux_x86-3.0.8.1.run: Permission denied

sudo: ./TeamSpeak3-Client-linux_x86-3.0.8.1.run: command not found

sudo sh TeamSpeak3-Client-linux_x86-3.0.8.1.run

Successful install.

But i cant enter the server folder to install the server


[COLOR=Red]eric@PowerEdge-1750-1:~$ sudo sh TeamSpeak3-Client-linux_x86-3.0.8.1.run
Welcome to the TeamSpeak 3 Client for Linux on x86 installer

In order to install this software you are required to accept the license
agreement, please press return to view the license.

You can scroll with the arrow keys and quit the viewer by pressing 'q'.
[RETURN]

Do you accept the license? (yes/no): y
Do you accept the license? (yes/no): yes
Creating directory TeamSpeak3-Client-linux_x86
Verifying archive integrity... All good.
Uncompressing TeamSpeak 3 Client for Linux on x86.........................................................................................................
eric@PowerEdge-1750-1:~$ 
[/COLOR]

---

