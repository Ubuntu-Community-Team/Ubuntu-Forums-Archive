---
title: "How to install Moblock"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by joshunator on 2008-07-27
So, I'm new to linux, I mean NEW!! I just installed Ubuntu 8.04 and wanted to installed peerguardian (just like what I have in windows). after some googling I found out the equivalent is Moblock, but the installation doesn't seem to be like downloading an installer file and double click. (a lot of terminal commands going on). could somebody explain me in plain english how to install moblock? your help will be greatly appreciated

Thanks in Advance

---

### Post by halitech on 2008-07-27
looks like the easiest way is to follow the instructions here:
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

to add the repos, run ```
gksu gedit /etc/apt/sources.list
``` and add to the bottom

deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main

then from the terminal, do a ```
sudo apt-get update
``` and ```
sudo apt-get install moblock
```

---

### Post by motang on 2008-07-27
> **joshunator said:**
> So, I'm new to linux, I mean NEW!! I just installed Ubuntu 8.04 and wanted to installed peerguardian (just like what I have in windows). after some googling I found out the equivalent is Moblock, but the installation doesn't seem to be like downloading an installer file and double click. (a lot of terminal commands going on). could somebody explain me in plain english how to install moblock? your help will be greatly appreciated

Thanks in Advance
Try this [out]("https://help.ubuntu.com/community/MoBlock"), let us know if you have any more questions.

---

### Post by joshunator on 2008-07-27
thanks for the help, sadly I got stuck....

I found the file /etc/apt/sources.list
to add the lines:
gksu gedit /etc/apt/sources.list
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main

so I open the file with the text editor but when I tried to save it says that I don't have enough permition, I'm assuming I'm not SU, how can I open text editor as SU? or how can I edit the sources.list with the permission?

Also, I'm interested on using the GUI, so that means after I do the source list I need to install mobloquer? how do I install the mobloqer?

Thanks in Advance

---

### Post by halitech on 2008-07-27
if you opened a terminal and ran 
```
gksu gedit /etc/apt/sources.list
```
it should have opened it as root and allowed you to make changes and save the file

```
sudo apt-get install moblock mobloqer
```

---

### Post by joshunator on 2008-07-27
> **halitech said:**
> if you opened a terminal and ran 
```
gksu gedit /etc/apt/sources.list
```
it should have opened it as root and allowed you to make changes and save the file

```
sudo apt-get install moblock mobloqer
```

Halitech,

     I think I'm getting an error when I try to install the program, this is what I get:

joshu@joshu-VAIO:~$ sudo apt-get install moblock mobloqer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package moblock


     Thanks for your help!

---

### Post by joshunator on 2008-07-27
Nevermind, Finally got it installed, I used Synaptic to install the packages, Thanks!

---

