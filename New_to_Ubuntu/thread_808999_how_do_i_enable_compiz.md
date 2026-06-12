---
title: "how do i enable compiz?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-05-27
please?

---

### Post by kesman on 2008-05-27
system -> preferences -> appearance -> visual effects

---

### Post by Mick8882003 on 2008-05-27
I wanted to get the cube working (had to reinstall ubuntu) how do I do that?

---

### Post by kesman on 2008-05-27
You need to install compiz config settings manager(ccsm) from synaptic and then go to visual effects -> custom and enable Desktop Cube and Rotate Cube plugins.

---

### Post by oedha on 2008-05-27
first.....what is your display adapter ? from terminal type :==> sudo lshw -short -C display
second....is the driver installed ?  from terminal :==> glxinfo | grep render
the answer must be yes
third .... install compiz from terminal type :==> sudo apt-get install compizconfig-settings-manager
then go to appearances.....select the last effect on visual tab.....
set your compiz by typing ccsm on terminal

---

### Post by kesman on 2008-05-27
> **oedha said:**
> 
**third .... install compiz from terminal type :==> sudo apt-get install compizconfig-settings-manager**
then go to appearances.....select the last effect on visual tab.....
set your compiz by typing ccsm on terminal

What? FYI compiz is installed by default in Hardy, and you don't need to run ccsm from terminal. Also, he also got compiz working, the only thing needed was the cube which needs to be enabled from ccsm.

---

### Post by oedha on 2008-05-27
:) just incase......i knew compiz was default..thx

---

### Post by Mick8882003 on 2008-05-27
thanks all, it worked, how do I install a compiz theme? I tried the right click from nautilis but it doesn't show?

---

### Post by kesman on 2008-05-27
Dunno about that, but do search on google and the forums, got me thousands of answers :P

---

### Post by oedha on 2008-05-27
i am not really expert on compiz theme
but i like to browse around on [http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by cheesypoof on 2008-05-27
[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200)
Fusion-Icon Package from Synaptic is nice too.

---

