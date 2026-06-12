---
title: "Ubuntu doesn't start up..."
date: 2013-05-25
forum: New to Ubuntu
---

### Post by kamrava on 2013-05-25
Hi there. [Sorry my English is not good]

I'm using scilab. When i do some operations like plot , Scilab was crashed. For solving this problem , i did all things in [this link]("http://wiki.scilab.org/Graphical%20issues%20with%20Scilab%205.X")
According to following part of [this link]("http://wiki.scilab.org/Graphical%20issues%20with%20Scilab%205.X"),
> [INDENT]Likely, there is a workaround to tackle this issue. One solution is to use a software accelerated driver. To do it, in /etc/X11/xorg.conf, look for the Section called Device and change the option Driver to mesa.
[/INDENT]

I must edit /etc/X11/xorg.conf, But there is no xorg.conf in /etc/X11/ for me!
For this reason, through below command i've created xorg.conf : 

[Ctrl + Alt + F1]
```

sudo service lightdm stopXorg -configure

```
I've copied /home/xorg.conf to /etc/X11/.
Also, According to following section of [this link]("http://wiki.scilab.org/Graphical%20issues%20with%20Scilab%205.X") :

> 
Section "Device" 
       Identifier      "Your Graphic card" 
       Driver  "vesa"
[...]
EndSection


I must enter my graphic card model in "Your Graphic card" and also "vesa". I don't know what exactly vesa is ! I've google it and someone said in [here]("http://www.opengl.org/discussion_boards/showthread.php/179672-Installing-OpenGL-mesa-on-ubuntu?p=1245516&viewfull=1#post1245516") for install vesa do below things and i did :
```

sudo apt-get install libglapi-mesa && sudo apt-get install libosmesa6

```
After all the steps above, i have restart computer and then Ubuntu doesn't start up and stay on Black Screen !
Through LiveDisk I've boot Ubuntu, I guessed maybe it's because of xorg.conf, I removed that as the default and reboot again, Ubuntu does't start up again !

---

### Post by lethall1 on 2013-05-25
i think there was written that some packages would be removed, when you made installation of mesa (but who cares? ))) )
you have to install appropriate video driver. Paste sudo lspci here.

---

### Post by kamrava on 2013-05-25
Fortunately i could fix that with recovery mode and below command's :

> Try to completely remove your ATI drivers from your system:


sudo apt-get purge fglrx*
Remove your xorg.conf


sudo rm /etc/X11/xorg.conf
Reinstall xorg completely


sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64


Re-configure Xorg


sudo dpkg-reconfigure xserver-xorg
Reboot


sudo reboot


New Problem :
I can't log in!!#-o#-o
It's say password is wrong ! But i'm pretty sure password is correct.

---

### Post by lethall1 on 2013-05-25
hm ))
Go to console and enable autologin
[http://www.liberiangeek.net/2012/10/enable-auto-login-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/enable-auto-login-in-ubuntu-12-10-quantal-quetzal/)

then try this
[http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04](http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04)

---

