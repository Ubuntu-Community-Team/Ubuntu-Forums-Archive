---
title: "problem with sudo in menu launchers"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by iansane on 2008-09-28
Hi,

I thought I was past this problem since I've been making my own launchers for a while.

Trying to add gksudo to the gedit command when editing menus isn't working.
Also, I tried using direct path, with 
```

gksudo /usr/bin/gedit

```

That doesn't work.

```

sudo gedit

```
in terminal does work 
but
```

gedit

```

from a root terminal doesn't work.

I have same problem with running a script from a binary that's stored in my home directory and running pdfsam from binary in home directory.

I know it has something to do with user settings because after changing the menu, my right click open with text editor is trying to use the non-working "gksudo gedit" command I put in the menu items properties.

Home is on seperate partition but seems like if it works in terminal it would work as a launcher. 

Can anyone explain this to me? Why it isn't working with certain apps?

Thanks

---

### Post by Pro-reason on 2008-09-28
What is the error message when you try that?

---

### Post by iansane on 2008-09-28
no error. Just nothing happens.

When I open terminal and type "sudo gedit" it works but when I put that command in a launcher or in the menu item's command nothing happens.

Had same probs with other scripts and executables in home directory.
They work when using terminal but not from menu item or launcher.

tried sudo, gksudo, and including full path tho the file and still nothing happens when clicking on the launcher or clicking in menu.

---

### Post by nowshining on 2008-09-28
what ver. of ubuntu are u using and are u using kde/gnome??

do you have all udates installed? have u tried logging out and back in?? have u tried a reboot of the computer??

---

### Post by iaculallad on 2008-09-28
Try setting the following configuration in your Launcher:

> Type: Application in Terminal
Name: Any name you want for this launcher
Command: gksudo gedit
Comment: Optional

Instead of just **Application**,set it to **Application in Terminal**.

---

### Post by iansane on 2008-09-28
well, now it decides to work. I have rebooted a couple of times and there were other unrelated things I've been working on like dhcpd3 so I don't know what happened.

It's hard when something doesn't work to just not touch it till someone helps but I can't think of anything that would have caused it and I've had the problem with other apps before but now it seems to be working.

Thanks

---

### Post by iansane on 2008-09-29
One other app that won't work from a launcher.

It's pdfsam binary. It's  /home/me/.pdfsam/bin/run.sh

How do I put in a command to run that from a launcher?

I tried "application in terminal" and "application"

Only way I can make it run is to click on it and choose "run" or run it manually from a terminal

How to run a .sh shell script from a launcher?

Thanks

---

