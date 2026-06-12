---
title: "Using Nice"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by szaqlon on 2008-07-05
I am trying to run a game and am getting lower framerates than I should be. I read that "nice" can be run from the command line to give a higher priority to an app. I keep getting errors when I try to run it. I have tried "C:\Program Files\World of Warcraft\WoW.exe" and I get the error "cannot set niceness: Permission denied". I am running Hardy and have tried everything I can find to increase the framerates, this is the last hope.

---

### Post by Xerp on 2008-07-05
I don't think that nice will work for you in this instance as there is probably something else you need to change. Which version of WINE are you using, for example? What settings have you already changed? What is your best frame rate? Take a look over here:

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

for some settings and info.

---

### Post by Marshal0505 on 2008-07-05
> **szaqlon said:**
> I am trying to run a game and am getting lower framerates than I should be. I read that "nice" can be run from the command line to give a higher priority to an app. I keep getting errors when I try to run it. I have tried "C:\Program Files\World of Warcraft\WoW.exe" and I get the error "cannot set niceness: Permission denied". I am running Hardy and have tried everything I can find to increase the framerates, this is the last hope.

Using Hardy, Nice will not increase your framerates.Using Nice commands might have worked on earlier Ubuntu versions with older kernels,but in Hardy it is best not to change Nice settings.If you want the best framerates in WoW,I think, it's best to tweak Wine and run WoW on a dedicated X server.These following links helped me tremendously.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=497332](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=497332)
[http://ubuntuforums.org/showthread.php?p=3377903](http://ubuntuforums.org/showthread.php?p=3377903)
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by szaqlon on 2008-07-05
I have been through wowwiki thoroughly, but I will check these other two. If it helped you hopefully it will work for me as well, Thanks.

---

### Post by Marshal0505 on 2008-07-05
> **szaqlon said:**
> I have been through wowwiki thoroughly, but I will check these other two. If it helped you hopefully it will work for me as well, Thanks.

No problem,post back here if you need further help :)

---

### Post by bodhi.zazen on 2008-07-05
If you want to user nice values below 0 you need to run as root.

sudo nice ....

---

### Post by szaqlon on 2008-07-05
I seem to be having a problem with the xswitch script. I have it in /usr/bin but what command do you need to actually launch the game?

---

### Post by szaqlon on 2008-07-06
I think I figured it out, but I keep getting an error message that says "The application "-d" could not be started". When I click ok another little box pops up that says "switch back to desktop?" Doesn't matter if I hit ok or cancel it brings me back to a login screen.

---

