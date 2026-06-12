---
title: "Resolution Issues / Theme Help"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by yami280 on 2008-06-06
Hi, I just installed Ubuntu and my resolution was really high when it first isntalled. Then I installed the Nvidia drives for my gfx card and now the resoultion is really low and everything looks really big.  I cant change higher than 1024 X 768.  

Also, I want to theme Ubuntu but I don't get how.  I installed COmpiz FUsion and Emerald but I'm lost.  I went to gnome-look and theres alot of different kinds of themess and I have no idea what to do.  Anyone help?

Also also, does anyone know what power tool is the one that keeps number lock on during startup.  I remeber reading it in some tutorial but I can't seem to find it anymore.

---

### Post by Golem XIV on 2008-06-06
try
```
sudo nvidia-settings
```
or
```
sudo nvidia-xconfig
```

just back up your xorg.conf file first, in case it gets screwed up
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

For numlock, take a look here:
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by yami280 on 2008-06-06
Okay I'll try that later.  I'm on Vista right now. The resolution for Ubuntu is really messed up.  I think the refresh rate is also messed up its hurting my eyes.

---

### Post by Hospadar on 2008-06-06
If nvidia-settings doesn't fix your problems (I think it will) you can try (in a terminal do a Ctrl-Alt-F1)
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```This dialog will allow you to change max resolutions and refresh rates through the X server, although the nvidia drivers generally handle these things a little differently (hence why you should use nvidia-settings)

Be sure to back up your xorg.conf as above before you attempt this

---

### Post by yami280 on 2008-06-06
Okay I'm trying to add
 if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
 onto the Default file but it won't let me cause i'm not root.  How do i get root permissions?

Also I'm trying the sudo nvidia-xconfig but this is what i get 
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by yami280 on 2008-06-06
ok.. i also need help with themes as well.. and.. i still need help with numlokc

---

### Post by yami280 on 2008-06-06
Okay can somene help me install grub gfx?  also.. i need resoultuion help still

---

### Post by Golem XIV on 2008-06-06
> **yami280 said:**
> Okay I'm trying to add
 if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
 onto the Default file but it won't let me cause i'm not root.  How do i get root permissions?

Also I'm trying the sudo nvidia-xconfig but this is what i get 
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

You get root with sudo (terminal) or gksu (GUI)

To edit the file you want using gedit, type
```
gksu gedit /path/to/file
```
in a terminal

For the nVidia drivers try nvidia-settings, as I said

For Compiz first install ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Now go to System -> Preferences -> Advanced Desktop Settings and configure Compiz the way you want.

---

### Post by yami280 on 2008-06-07
Okay thanks I fixed the resoultion and themed my desktop.

---

### Post by japhyr on 2008-06-07
I'm trying to sort out a resolution issue as well.  Can you say specifically what fixed your resolution problem?

---

### Post by yami280 on 2008-06-07
Hm.. Oh well i backed up the xorg file.  Then I edited it and changed the resoultion from nvidia-auto-select of something like that .  to 1280x1024

---

