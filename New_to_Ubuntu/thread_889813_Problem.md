---
title: "Problem"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by honkey on 2008-08-14
I have a very bad Computer
At first there where windows xp on it but it works not a long time because of vires and worms
Then I installed ubuntu and everything was right
but after a while I cant open the GUI of ubuntu and i only get terminal after reboot
so I tryed many other systems
but no system works fine
Ive installed ubuntu again
but When I updatet the system The graphics lokks like windows, I cant make settings anymore I cant go in Firefox or something else
Debian, which I have jet works also not really
Can You tell me what I did wrong with my computer?????
Help me 
I want to Work woth my computer and not waste so many Time with problems!

---

### Post by jamesrfla on 2008-08-14
If you get a command line when you boot Ubuntu check to make sure in GRUB that you are not botting the recovery option. When you do get the command line when you boot Ubuntu log in and type ```
startx
```

---

### Post by sayakb on 2008-08-14
Did you upgrade you ubuntu to a newer version? Upgrading (not updating) often breaks the system packages (though works in most cases) What are your computer specs? Download the latest iso (Ubuntu 8.04.1) from here and install it: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

Plus, please give descriptive titles to your thread (Unlike "Help needed" or "n00b here")

---

### Post by billgoldberg on 2008-08-14
You are going to have to be more specific.

What specs does you computer have?

What Ubuntu version are you using.

What else did you install on the system.

Anything you did on it, tell us.

Also provide use with the output of this command

```
lspci
```

---

### Post by honkey on 2008-08-14
I installed the newest version of ubutnu but when the system installs the updates it freezes the screen and I cant do anything
When I restarted the computer the system has no funktion anymore

---

### Post by sayakb on 2008-08-14
First goto System->Administration->Software Sources->Updates and **uncheck** the Pre-released and Unsupported updates. (ie. check the first two sources only).
Press Reload button when prompted to. Now open a terminal (Applications->Accessories->Terminal) and type in:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by honkey on 2008-08-14
I have now debian on my computer
are you shure ubuntu works if I install it one more time?
Ive very frustrated of all this systems
can you animate me a little bit;)

---

