---
title: "Trying to install Realtek 8811au driver"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by mark194 on 2018-08-28
I'm very new to Ubuntu and trying to install a wireless USB adapter on my system.  The adapter came with an install.sh script, which I ran in terminal but it seemed to have a problem with the PW I supplied when it asked for one. Only PW I have set up on the system is the one I use to log in so that's the one I gave when requested.  This is what the terminal session looked like:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.




mark@mark-OptiPlex-390:~$ '/home/mark/Desktop/install.sh' 


##################################################
Realtek Wi-Fi driver Auto installation script


Novembor, 21 2011 v1.1.0


##################################################


/home/mark/Desktop/install.sh: line 17: cd: driver: No such file or directory


Decompress the driver source tar ball:


tar: Old option 'f' requires an argument.


Try 'tar --help' or 'tar --usage' for more information.


Desktop


Documents


Downloads


examples.desktop


Music


Pictures


Public


snap


Templates


Videos


/home/mark/Desktop/install.sh: line 25: cd: too many arguments


Authentication requested [root] for make clean:


Password: 


su: Authentication failure


Authentication requested [root] for make driver:


Password: 


su: Authentication failure


##################################################


Compile make driver error: 1


Please check error Mesg


##################################################


mark@mark-OptiPlex-390:~$


Being so new to Ubuntu, I'm at a loss.  The USB adapter wasn't immediately recognized by the system as far as I could tell (rebooted after I plugged it in and no wifi networks show up still).  Any suggestions?

thanks-

Mark

---

### Post by cariboo on 2018-08-29
I'd suggest opening a terminal and running:

```
sudo lshw -C network
```

to see if your device is detected.

---

### Post by Yellow Pasque on 2018-08-29
It seems like you copied the install.sh file and nothing else to your Desktop dir? 
Anyway, if there was a Linux driver on the CD, it's probably too old to work with modern kernels.

If you have a wired internet connection, please run the info script here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

