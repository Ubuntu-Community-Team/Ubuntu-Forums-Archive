---
title: "Added xorg-edgers PPA, now boots to console"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by shamstaj on 2013-11-12
I have installed Liunix ubuntu today, after  having spent more than 12 hours i was able to install couple of  applications and drivers, getting help here on Ask Ubuntu, the last  thing i thought of looking for " why my left mouse dose not work for  firestorm second life viewer " and i followed a few step above and than  become a catastrophe :( Pleeees help after re booting my screen went black with just ubuntu command prompt,  everything is gone, unity, dash board , my documents.  left side bar etc. the step which i followed was here 
[http://askubuntu.com/questions/184222/left-mouse-button-not-working-in-xubuntu-session/376275#376275](http://askubuntu.com/questions/184222/left-mouse-button-not-working-in-xubuntu-session/376275#376275)
please note this is my first  time from window to ubuntu, i have no idea at all. thanks i will be  waiting here till i get any answer, this is window os i am posting this  question from.  i know there is some reverse engineering which will fix this issue, so please help  me with the command so that i can enter at the ubuntu prompt with black screen and i get back my ubuntu desktop.

...............................................the step i follwed was this,
  Check if you have xserver-xorg-input-evdev installed on your system:
  sudo dpkg -s xserver-xorg-input-evdev
  
1. If yes, do: 
sudo add-apt-repository ppa :org-edgers/ppa sudo apt-get update sudo apt-get upgrade
  2.If no, do: 
sudo add-apt-repository ppa: org-edgers/ppa sudo apt-get update sudo apt-get install xserver-xorg-input-evdev
  
Reboot.

in my case the second option executed. it seems i have installed something repsitory or xserver removing this may fix my problem , but dont know how to do this.

---

### Post by deadflowr on 2013-11-12
Which was it, yes or no?

But anyway, install the package ppa-purge.
```
sudo apt-get install ppa-purge
```
then run
```
sudo ppa-purge xorg-edgers
```

this should revert the system to state it was before the upgrade to the edgers packages.

Edit: OOPS, forgot to say login to the command prompt like you would logging into Ubuntu, except it's a sort of terminal in full screen.
put in your username and the user's password.(password field will be blank, type it as you know it and hit enter)
Then follow the above advice.

---

### Post by shamstaj on 2013-11-12
Thanks allot flower, i will try now,
btw my ubuntu is 13.10 installed it today.

and to fix the left mouse button for second life i executed above command the one which ran was this

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install xserver-xorg-input-evdev   Reboot.

---

### Post by oldos2er on 2013-11-12
Changed thread title a bit to better reflect the question.

---

### Post by deadflowr on 2013-11-12
More on xorg-edgers
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Probably be good to know what it was you installed.

---

### Post by shamstaj on 2013-11-12
nop, :( did not work, though both command executed successfully , but after rebooting and entering password and username it went to the same screen. 
Ubuntu 12.04.3 LTS Ubuntu tty1
Shams@uhuntu $ _

---

### Post by shamstaj on 2013-11-12
is there a re install possibility ? if yes then how, like i did before ? will it remove my install program and drivers ?

---

### Post by deadflowr on 2013-11-12
Before doing any re installation stuffs, try this command
```
sudo service lightdm restart
```
and see if it brings up a login screen.

If not, then hit ctrl+alt+F1 to get back to TTY1.

Edit: It might also be helpful to know what graphics card you have, and whatever drivers you installed prior to the xorg-edgers debacle.

---

### Post by shamstaj on 2013-11-12
That did not work, 
my systme config 
i7 processor 
Nvidia GeForce GT640 graphic card, 
3 gb ram
500 gb HD.
If nothing works is it easy to reinstall and keep my application installed and not removed during installation ?

Btw, your first two command which ran succesfully i saw a quick message some thing like 
PP to be removed : xorge, PPA
and next line,
PP can not be removed 

Thank you

or something like that, not sure.

---

### Post by monkeybrain20122 on 2013-11-13
> **shamstaj said:**
> nop, :( did not work, though both command executed successfully , but after rebooting and entering password and username it went to the same screen. 
Ubuntu 12.04.3 LTS Ubuntu tty1
Shams@uhuntu $ _

Is it Ubuntu 12.04.3 or 13.10? If it is 12.04.3 it won't work because of the updated graphic stack, you have to first revert it to the lts stack before you can update with xorg-edgers.

---

