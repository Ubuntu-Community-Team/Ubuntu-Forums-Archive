---
title: "GUI problem 8.04 client"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by petdog on 2008-06-16
Hey guys i accidentally deleted my task bar item in my GUI and i can not access the add/remove applications service, please help me cause i need to get this up and going so i can work, i installed Ubuntu today first time user of the client.

Thanks PetDog

---

### Post by RSingh on 2008-06-16
Right click on panel >> add to panel >> menu bar

---

### Post by petdog on 2008-06-16
Thanks for fast reply however i do not have a panel, the thing at the top is totally gone!! :( i can not even see it i am using my limited knowledge of server to try and get the apt to work and get the application i unistalled that i think was the issue it was evolution mail, i think it messed up the panel!!

---

### Post by RSingh on 2008-06-16
oh, okay, then try:

Alt-F2 

```
gnome-panel
```

that should bring back the panel

---

### Post by petdog on 2008-06-16
Hey man i must be stupid or something i keep pressing Alt-F2 and nothing happens then i try F1 and it says i am running AC power in bottom right.

---

### Post by RSingh on 2008-06-16
strange, try restarting your Xserver by "Ctrl-Alt-BackSpace" key and then trying again. **(Careful: You will have to login again, so save any work)**

---

### Post by petdog on 2008-06-16
Hey, well i did as u said i am running client just incase u did not know, this is very very wierd, i am trying to re-install the program i uninstalled can u help me with getting terminal up maybe? or ever add/remove programs, try sending me a shortcut or something? e.g. like windows!

---

### Post by RSingh on 2008-06-16
From what I know, you dont have to install anything to bring back the panel, its already installed, you just have to run it. Ok, do one thing, right click on the desktop, add launcher

Give any name and as for command give "gnome-terminal"
Click ok and this should be your should for the terminal. Open the terminal and write "gnome-panel" and press enter.

---

### Post by petdog on 2008-06-16
There is no launcher running friend i right click and say create launcher and nothing happens!

---

### Post by petdog on 2008-06-16
did the around the world way by launching the thing in my bin here is the output

andrew@andrewubu:/usr/bin$ gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found
andrew@andrewubu:/usr/bin$ 


i will try the sudo!!

---

### Post by petdog on 2008-06-16
Yes we getting somewhere now i have done most of it i will restart and see wat comes up!! Thanks

---

### Post by petdog on 2008-06-16
Its working thank you so much for your help man!! :D :D :D :D

---

### Post by RSingh on 2008-06-16
glad it worked out:guitar:

---

