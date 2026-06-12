---
title: "[SOLVED] how to close x server to install nvidia driver"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by imgkg on 2008-09-03
hi guys,yes i know you might suggest to look in other threads which got same problem but as i followed the instructions given like ctrl+atl+f1 as i do this command my screen changes to some color stripes and it remains that way forever i guess   please help how to close xserver and install my nvidia driver

---

### Post by Titan8990 on 2008-09-03
Open a terminal and type:

sudo /etc/init.d/gdm stop

You will still need to hit CTRL+ALT+F1-5 to get into a terminal.

---

### Post by imgkg on 2008-09-03
i did that as you said but still same problem those color stripes as if screen has freezed it remain forever

---

### Post by Gannon8 on 2008-09-03
Hit Ctl-Alt-F1, then type:
```
sudo /etc/init.d/gdm stop
```
And then run the nvidia file.

---

### Post by imgkg on 2008-09-03
i tried that Ctl-Alt-F1 but all i get is colored stripe screen not some command line mode as you think some one please help

---

### Post by Shazaam on 2008-09-03
Reboot, choose "Recovery Mode" in the grub boot screen.

---

### Post by jemate18 on 2008-09-03
> **imgkg said:**
> hi guys,yes i know you might suggest to look in other threads which got same problem but as i followed the instructions given like ctrl+atl+f1 as i do this command my screen changes to some color stripes and it remains that way forever i guess   please help how to close xserver and install my nvidia driver

This might help you..
> [http://ubuntuforums.org/showthread.php?t=905295](http://ubuntuforums.org/showthread.php?t=905295)

---

### Post by imgkg on 2008-09-03
i managed to get in to command line mode using recovery mode in boot menu but as i want to login into root its says incorrect login

---

### Post by Tatty on 2008-09-03
The root account is disabled by default in ubuntu, you should execute any commands requiring root, by prefacing them with sudo (or gksu if it launches a graphical app)

You should probably have a read of this...[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by imgkg on 2008-09-04
i have used that sudo before any command but still its not logging me as an root command line mode whereas on desktop i am able to open my all other applications like synaptic manager etc using my same password

---

### Post by jemate18 on 2008-09-04
> **imgkg said:**
> i have used that sudo before any command but still its not logging me as an root command line mode whereas on desktop i am able to open my all other applications like synaptic manager etc using my same password

did you try the link I posted above? It has a good information.....

---

### Post by imgkg on 2008-09-04
yes offcourse i did tried it its very useful information but as i tried those commands i have to login as root and thats where its showing me to incorrect login, i am thinking of activating root system wide then disabling it later but i dont know how to do that

---

### Post by jemate18 on 2008-09-04
> **imgkg said:**
> yes offcourse i did tried it its very useful information but as i tried those commands i have to login as root and thats where its showing me to incorrect login, i am thinking of activating root system wide then disabling it later but i dont know how to do that

In the link I post above.. (in that thread) I discussed something about the
"root Drop to root shell prompt" menu ..... did you selected it? You should be root if you have...

---

### Post by Tatty on 2008-09-04
> **imgkg said:**
> i have used that sudo before any command but still its not logging me as an root command line mode whereas on desktop i am able to open my all other applications like synaptic manager etc using my same password

You do not need to log in as root at all in ubuntu.  Simply log in as yourself and use 
```
sudo <command>
```

It will then ask you for your password, type that in and it will execute that command with superuser (root) privilages.

---

### Post by imgkg on 2008-09-04
now i lost my account too it says ```
user@user-desktop:~$ sudo su
[sudo] password for user: 
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
root@user-desktop:/home/user# 

```

---

### Post by alienexplorers on 2008-09-04
Why don't you just run Envy and let it take care of loading the drivers and nvidia-settings.

---

### Post by imgkg on 2008-09-04
out put of command " ps -ef | grep gdm "is 
```
root  7127   7116 0 10:43 tty1   00:00:00 grep gdm 
```

---

### Post by imgkg on 2008-09-04
now how to get this envy

---

### Post by imgkg on 2008-09-04
thanks for staying with me anyways problem isnt solved so its ok i guess let it be as it is

---

### Post by lengo on 2008-09-04
> **alienexplorers said:**
> Why don't you just run Envy and let it take care of loading the drivers and nvidia-settings.
Kindly keep in mind that this is the "Absolute Beginner Talk" area of the forum. It's kind of frustrating as a beginner (and I count myself among them!) to have a legit question and be told to forget it and do something else (that's not accompanied by clear instructions itself . . . ) Besides, it seems the OP has a deeper problem than just installing video drivers! I can't help him/her, but surely someone else can. :) Good luck, imgkg!

---

### Post by imgkg on 2008-09-04
i am finally able to install nvidia driver using envy more information on this thread [http://ubuntuforums.org/showthread.php?t=833416](http://ubuntuforums.org/showthread.php?t=833416) thank you everyone

---

### Post by tuxtix on 2010-06-07
> **imgkg said:**
> i have used that sudo before any command but still its not logging me as an root command line mode whereas on desktop i am able to open my all other applications like synaptic manager etc using my same password

type "sudo -s" then u will be logged in as root user.

*Good luck!* :)

---

