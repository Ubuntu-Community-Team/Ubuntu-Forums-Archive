---
title: "upgrade to 8.04 failed"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by maxhoward on 2008-07-24
I started the upgrade from Ubuntu 7.0 to 8.04. The packages downloaded successfully (apparently).  Then it started Installing the Upgrades.  That process went on for a good while and then I noticed that nothing seemed to be happening.  The Terminal said "configuring locales" and the progress bar stated "12 min remaining".  The display stayed that way for well over 30 min - perhaps an hour - I am not sure.  So I thought it was hung up - it did not respond to any keyboard or mouse action.  So I turned the power off with the power button.  The next time I powered up, I got past the Ubuntu login screen and the password screen but then everything stopped.  I powered down and tried again but this time selected Windows XP from the Dual Boot screen and that worked successfully.

So how can I get Ubuntu running again?

---

### Post by gerben1 on 2008-07-24
You could try to backup your Ubuntu home directory from WindowsXP, with a program like this:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
(make sure you copy all the hidden directories, those are the directories that start with a dot, like .gconf for example, they contain the programs' settings)

then download the Ubuntu 8.04 iso, burn it to CD, boot from the CD, do a new fresh install of Ubuntu 8.04 on the partition where Ubuntu 7.0 was, install the programs you use and then copy back the backup of your home directory so that all your program settings, email, etc. is back.

---

