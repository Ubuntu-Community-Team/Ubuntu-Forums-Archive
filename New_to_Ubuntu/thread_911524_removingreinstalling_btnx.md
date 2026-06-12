---
title: "removing\reinstalling btnx"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Kronie on 2008-09-05
i am the unlucky owner of MX revolution, and i cant live without the middle button! i installed btnx a wile back, and it was my first ever software that i had to compile on linux. so something went wrong, and the software wouldn't ever start again after i closed it for the 1st time. 
how do i uninstall it completely, or is there a way to fix it without uninstalling?

---

### Post by Shazaam on 2008-09-05
Have you tried starting btnx in terminal? Might print out error messages.

---

### Post by Kronie on 2008-09-05
```
kron@kron-desktop:~$ btnx
 btnx: uinput modprobed successfully.
 btnx: Opening config file: /etc/btnx/btnx_config_Default
 btnx: Could not read the config file: No such file or directory
 btnx: Configuration file error.

```

---

### Post by Kronie on 2008-09-05
**Bumpz!**

---

### Post by Shazaam on 2008-09-05
Uninstall=
Installed from source- open terminal, cd to the folder that you extracted btnx to and run...
```
sudo make uninstall
```
Go here for a better way to install btnx...
[http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)
I used that page to install it using a .deb

---

### Post by anotherdisciple on 2008-09-05
Just an FYI... you can add a repo for btnx.... add this to your /etc/apt/sources.list

```
# BTNX Mouse Control
deb http://ppa.launchpad.net/daou/ubuntu hardy main
deb-src http://ppa.launchpad.net/daou/ubuntu hardy main
```

Just replace 'hardy' with whatever version you are using. That's how I did it... it's trustworthy... no worries.

Also try typing this in your terminal...
```
locate btnx
```

I tried it on mine... I found a few config files... maybe deleting one of them is the key... maybe it's just corrupted.

---

### Post by Shazaam on 2008-09-05
"I tried it on mine... I found a few config files... maybe deleting one of them is the key... maybe it's just corrupted."
Yes, look in your btnx folder. There may be a config file you could rename to default.

---

### Post by Kronie on 2008-09-06
right, so i uninstalled it, and then tried to get it from repos through terminal andit gave me 404 error. then i did t thru synaptic and it downloaded and installed perfectly. btnx found my mouse, and now i finally have middle mouse button! BUT, i would also like to have my search button to do keystroke "ctrl+w" to close tabs in FF, and have my thumb wheel to mute\raise\\lower the volume.  i set everything the way it said in the manual, but i still have this annoying search box, and a flipin not-working thumb wheel! also, btnx gives me an error when i try to restart it by pressing the "restart btnx" button in the main menu.

---

### Post by Kronie on 2008-09-06
*bump* :popcorn:

---

