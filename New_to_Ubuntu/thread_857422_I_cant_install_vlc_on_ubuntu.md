---
title: "I cant install vlc on ubuntu"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by swapna123 on 2008-07-12
Hi All,

I can't install vlc on my computer.
My synaptic package manager is not working and I can't install anything.


I got the following error message when I tried to install vlc movie player
-------------------------------------
E:Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
-----------------------------------

Please help me with this.
Do I have to make any changes to the source code to make ubuntu function as it used to, when I first installed it?
If yes, somebody please give me the unmodified source code, so that I can just copy this code into my source code file and get it working soon.


Thanks in advance!!
Swapna

---

### Post by avtolle on 2008-07-12
Some other package manager is open is the normal cause of the error message. Did you close Synaptic (you mentioned it wasn't working)?

---

### Post by SunnyRabbiera on 2008-07-12
This is a common error, dont worry its nothing serious but make sure that another package manager isnt running like update manager or something like that.

---

### Post by VitaLiNux on 2008-07-12
Maybe you have synapic opened. Check if it's opened. If you see no synaptic opened through GUI, check the system monitor to see if there's a synaptic instance opened. If so, kill the process. Now,  if you're using the terminal, use **sudo apt-get install vlc** with a user with administrator privileges. That should work!

---

### Post by aktiwers on 2008-07-12
Yeah close all apps that use the repositories, like apt-get, synaptics, add/remove and so on. 

You can only have one packagemanager app running. And only one instance of that packagemanager

---

