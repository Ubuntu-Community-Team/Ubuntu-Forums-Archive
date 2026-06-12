---
title: "Nvidia driver problems"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by philman1008 on 2011-09-20
I am having issues with the nvidia drivers on 11.04. 
First I tried the easy way, additional drivers using version current. This starts up and unity runs, but it wont display the background image and anything when you open a browser or similar.
SO I have also tried the synaptic manager, this was no better.
I have then tried apt-get install nvidia-current. Then on loading Nvidia setting to configure, it says I need to run nvidia-xconfig as root. So did sudo nvidia-config and just got invalid command.
Whats my next port of call?

---

### Post by realzippy on 2011-09-20
Welcome to UF ...
:) post error from:
```
sudo nvidia-xconfig
```

---

### Post by philman1008 on 2011-09-22
Managed to nvidia-xconfig to work.
Now the system just hangs on startup.
Can start it in recovery failsafe graphics mode, but not with nvidia. :-(
What can I try next please?

---

### Post by philman1008 on 2011-09-22
OK now got it to start up, but have no background again.... I can see unity, but I cant start anything up using graphics.
Hmmmm.....

---

### Post by jockyburns on 2011-09-22
I too have , what appears to be a problem with Nvidia drivers. It says my driver has been downloaded , but not installed, yet it's highlighted with a green circle (which from other posts , s) suggests it is installed and working properly. 
Some have suggested opening system/administration/
 But when I look in system, I don't have the administration option. 
Running Ubuntu 11.04 Natty Narwhal , if that makes any difference.

---

### Post by philman1008 on 2011-09-22
Thats about where I am at.
Ive been all around the houses... nearly broke it and ended up back on the basic nuoveau drivers.
might just wipe and reinstall and start from scratch with it.
Have you run sudo nvidia-xconfig yet?
Didnt help me, but dont know if I did something prior that broke some packages.
Worth a bash mate?

---

### Post by jockyburns on 2011-09-22
Tried the sudo nvidia-xconfig in terminal and got this response
"Using X configuration file: "/etc/X11/xorg.conf.

"VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'"


New to Ubuntu so couldn't even tell what this means.

---

### Post by philman1008 on 2011-09-23
Ubuntu has written you a new Xorg.conf file. This is the file that contains all your video settings. Is your display any better?

---

