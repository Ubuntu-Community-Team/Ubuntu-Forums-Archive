---
title: "Can't Access Terminal!"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by djmac on 2012-02-12
I just did a fresh install of Xubuntu and I cannot access the terminal at all - I am completely at a loss as to what to (I am used to regular old Ubuntu).

I tried to graphically access a terminal via "terminal emulator" in the menus - but all I get is an error:

> **Failed to execute default Terminal Emulator.**

Failed to execute child process "terminal" (No such file or directory).

Any ideas?

Cheers

---

### Post by raja.genupula on 2012-02-12
[http://crunchbanglinux.org/forums/topic/10725/resolved-xfce4-altf2-error-failed-to-execute-default-terminal/](http://crunchbanglinux.org/forums/topic/10725/resolved-xfce4-altf2-error-failed-to-execute-default-terminal/)

see post no 8 in that 


hope that helps .

if anything comes up , please let us know.
All the best.

---

### Post by djmac on 2012-02-12
Hi Raja,

Thanks for the quick reply. 

I was able to get to the normal terminal by using alt-F2 and running the following:

```
xfce4-terminal
```

I couldn't find the following file (suggested in the other post):

> gedit ~/.local/share/xfce4/helpers/custom-TerminalEmulator.desktop

Do you have any suggestions on which file I should change for xbuntu?

Thanks again.

---

### Post by Toz on 2012-02-12
From your error message, it appears that it is trying to run the application "terminal" which doesn't exist. 

Try setting xfce4-terminal in Preferred Applications. Go to Settings->Settings Manager->Preferred Applications->Utilities tab and set the Terminal Emulator to "Xfce Terminal"

---

### Post by ghilliker on 2012-03-01
I finally got the TERMINAL in XFCE but still do not have any applications.  the only thing I can see is the desktop and File Edit View Go Bookmarks Help across the top of the screen.  Right click does not work nor does anything else display.  

If I sign on as GUEST, I get the normal XFCE panel.  How do I get it back for my user?

---

### Post by jerome1232 on 2012-03-01
Sounds like some user configurations are messed up, I would personally take the easy way out and create a new user (make sure it's in the admin group), delete old user, delete old users home directory to ensure all configurations are wiped out,then recreate the original user (again make sure it is in the admin group).

---

### Post by ghilliker on 2012-03-01
Thanks Jerome...  I figured as much.  Can that be done from a terminal (sudo...) or should it be done from root?

Thanks in advance

---

### Post by ph4nt0m117 on 2012-03-01
Install terminator, profit.

---

### Post by jerome1232 on 2012-03-01
> **ghilliker said:**
> Thanks Jerome...  I figured as much.  Can that be done from a terminal (sudo...) or should it be done from root?

Thanks in advance

I'm not sure what you mean, it can be done via your gui tools (I don't know xubuntu) or via command line tools.

First you would create the new user (if my syntax is right, it's been awhile since i've used adduser, but that should create a user called temporary in the admin group)

```
sudo adduser temporary admin
```

Logout, log in as temporary

```
sudo deluser youroldusernamehere --remove-home
sudo adduser youroldusernamehere
sudo usermod -a -G plugdev,lpadmin,admin,adm,dialout,cdrom youroldusernamehere
```

logout then log back in as your old user, make sure everything works, it it's okay, then delete the temporary user
```
sudo deluser temporary --remove-home
```

---

