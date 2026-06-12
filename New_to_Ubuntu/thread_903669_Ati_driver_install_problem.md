---
title: "Ati driver install problem"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by zdog291 on 2008-08-28
Okay so I was trying to install new ati drivers for my x1300 radeon graphics card I bought and when I try to run the command: ```
aticonfig --intitial
```

I get the error that "Configured Video Devices" needs a driver line. Also I should mention that currently I am in the white screen of death when I log in to I always press ctrl+alt+f1 to get to the terminal

---

### Post by overdrank on 2008-08-28
> **zdog291 said:**
> Okay so I was trying to install new ati drivers for my x1300 radeon graphics card I bought and when I try to run the command: ```
aticonfig --intitial
```

I get the error that "Configured Video Devices" needs a driver line. Also I should mention that currently I am in the white screen of death when I log in to I always press ctrl+alt+f1 to get to the terminal

Hi and you can try and boot into recovery mode and use the xfix option. Recovery mode is the the usually the second choice at the grub.

---

### Post by nicedude on 2008-08-28
You could also in grub boot menu press "e" and then select kernel you want to boot to and press "e" again to modify the boot commands and add vga=ask to the end of the list of boot commands and then press "b" to boot using the modified boot command. When you boot in such a fashion you should be asked about what vga mode to use by pressing enter to do so when prompted, do that and then choose one of the vga modes it says are supported at least then you will get a semi decent graphical login session going if that would help you fix the problem rather than having to do it via a command line.

---

### Post by zdog291 on 2008-08-28
I tried both of those solution and still got thw white screen of death, does any one know ho I could edit the xorg.conf file form the terminal so I could just manualy add Driver   "ati"

---

### Post by nicedude on 2008-08-28
yes you could use vim text editor to edit it here is the command to open it,

sudo vim /etc/X11/xorg.conf

be aware though that vim is pretty basic and so is not as easy to use as gedit is.

---

### Post by jbrown96 on 2008-08-28
> **nicedude said:**
> yes you could use vim text editor to edit it here is the command to open it,

sudo vim /etc/X11/xorg.conf

be aware though that vim is pretty basic and so is not as easy to use as gedit is.
I love Vi, but it's not a suggestion when messing with xorg.conf for the first time. Use pico ```
sudo pico /etc/X11/xorg.conf
```
You should make a backup of your configuration first. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
``` If the file needs to be recovered just reverse the two file names from the last command

---

### Post by tuxxy on 2008-08-28
If you cant get into any GUI you could reconfigure the xorg and then start again to find a driver

---

### Post by jbrown96 on 2008-08-28
> **tuxxy said:**
> If you cant get into any GUI you could reconfigure the xorg and then start again to find a driver
Good idea. The command would be ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by markbuntu on 2008-08-28
You need to use:

aticonfig --initial

not

aticonfig --intitial

Now that you may have aticonfig somewhat confusedly configured you should use:

aticonfig --initial -f

This will add the proper lines to your xorg.conf and save the old one.

---

