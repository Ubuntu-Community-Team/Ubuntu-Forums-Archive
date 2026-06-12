---
title: "GUI crashed"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by msidhard on 2008-05-26
am using Dapper on celeron D processor with 256 MB ram. due to power failure my system gui crashed. so if the system boots and enters gui then it hangs in a black screen. no response of sensing the key strokes in num lock. if it boots as root in terminal it works but if i enter in gui the system hangs. i tried in loading in recovery mode but X ends up in a blank screen. after hitting keys ctrl+alt+f1 the root terminal says some errors in /*/* etc . how to recover it back to GUI.

---

### Post by spiderbatdad on 2008-05-26
Possibly run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```from cli.

---

### Post by msidhard on 2008-05-27
i tried that thats not working. ANY other helps. could you say what happened in my system(as u guess)

---

### Post by hyper_ch on 2008-05-27
Hmmm, you could just create a new user home so that new default configs will be generated.. maybe that helps.

(1) Boot into recovery mode

(2) Move your current user home to a different name
```

mv /home/USER /home/USER2

```
(assuming your username is "USER" --> just replace it accordingly

(3) reboot and then it should work again... at least it should re-create a new home user dir for you with default configurations.

(4) copy files back from the backup location to your new home ;)

---

### Post by msidhard on 2008-05-27
I Tried And Tired. My System Is Good Untill It Try To Initiate Gui . It Hangs After The Loading Mouse Symbol And Before Gui Login Window. It Hangs In Empty Screen.

---

### Post by hyper_ch on 2008-05-27
did you try what I said?

---

### Post by msidhard on 2008-05-27
i tried but failed. the x is loading good. but it hanged before login GUI window . but login was successful from root terminal. i think the file relating to the program loading next to x is corrupted. help me thanks in advance

---

### Post by msidhard on 2008-06-01
It says error loading /dev/wacom there is no such file or directory. i moved home/user and dpkg-reconfigure -all . and apt-get install wacom-tools, now its saying error loading /tmp/.x11-unix

---

