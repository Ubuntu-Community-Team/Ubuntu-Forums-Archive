---
title: "what do this comand mean and  how  to  disable  it"
date: 2017-03-30
forum: New to Ubuntu
---

### Post by 243750496 on 2017-03-30
sudo xhost +SI:localuser:lightdm
Any command  to reset  it  to default 
Like 
sudo xhost -SI:localuser:lightdm


Do my command  right?

---

### Post by Frogs Hair on 2017-03-30
Where are you seeing this message and/or command and what are you trying to accomplish?

---

### Post by 243750496 on 2017-03-30
Remove the dot of login screen 
sudo xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-grid false;exit

---

### Post by again? on 2017-03-30
I don't think there is any need to revert anything. See "man xhost"
You could run this to remove lightdm  from the access control list.
```
sudo -i
xhost -SI:localuser:lightdm 
```

FYI these are the sequence of commands (tested in 16.04) to remove the greeter dots.
```
sudo -i
xhost +SI:localuser:lightdm
su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-grid 'false'

```
You can then type in "exit" and press Enter. Repeat.
or
just close the terminal.

---

