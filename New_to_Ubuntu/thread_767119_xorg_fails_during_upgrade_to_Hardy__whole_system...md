---
title: "xorg fails during upgrade to Hardy  whole system... buggered"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-04-25
while upgrding to 8.04, I got lots of error messages about upgading xorg - every single part of it. When there was about 2mins remaining of installing new packages, the upgrade stopped, said that it had failed, that the computer may be unusable 'n' shut down. It also said that ubuntu-desktop did not upgrade/install, despite the fact that i made sure to install beforethe upgrade.

Now when i turn on the computer, grub has 4 entries for ubuntu 8.04 (two regular, two recovery mode + memtest). When I run the first one, it seems to boot up normally, but i have to log in via the terminal/login thing, it then claims that it cant load the GUI because of xorg problems, and takes me back to the command line. When i try apt-get install xorg it comes up with a load of errors, and also says that there are 63 not fully installed packages.

when i run the second 8.04 entry, i simply get a blank screen with nothing happening. :-(. help! is there any way of restoring my machine to it's former glory without a full reinstall? this is so annoying! waah!

all help very much appreciated, thanks!

---

### Post by decoherence on 2008-07-06
first you have to fix your package database.

```
sudo apt-get -f install && sudo apt-get upgrade
```

assuming you don't get any errors with that, next try reconfiguring X.

```
sudo X -configure && sudo Xorg -config xorg.conf.new
```

and see if you get a little X cursor. If you do, it probably worked, at least to a certain degree. Press CTRL ALT Backspace to get back to the console. Now copy the file *X -configure* generated to /etc/X11/xorg.conf (making a backup, of course)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo cp xorg.conf.new /etc/X11/xorg.conf
```

run startx again, cross fingers. if it doesn't work, post error messages.

---

