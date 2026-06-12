---
title: "Help regarding upgrade"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-05-22
hi,
i dont have fast internet connection,
but i have got hardy heron cd,

i want to upgrade from that cd(from 7.10 to 8.04)
dont know how, please help

---

### Post by sharks on 2008-05-22
This will help u:

[www.ubuntu.com/getubuntu/upgrading](www.ubuntu.com/getubuntu/upgrading)

---

### Post by lucky.developer on 2008-05-22
in that page, they asked me too run som gksu command, when i run that command nothing happens..??

---

### Post by muteXe on 2008-05-22
I'd strongly recommend a fresh install to be honest.  But that's just me.  Things went horribly wrong when i upgraded from Feisty to Gutsy.  Fresh install to Hardy was all good though.
Just remember to burn your home folder and other needed files to a cd or something.

---

### Post by prshah on 2008-05-22
> **lucky.developer said:**
> hi,
i dont have fast internet connection,
but i have got hardy heron cd,
i want to upgrade from that cd(from 7.10 to 8.04)
dont know how, please help

Just put the CD in the drive, and you will get a popup box; one of the buttons will be marked as "upgrade". Select that, and it will upgrade your ubuntu.

If you don't get the upgrade option, you can manually go to the mounted folder and give the command for upgrade, eg: Open a terminal, then
```

cd /media/cdrom
sudo ./cdromupgrade
```

replace "/media/cdrom" with the actual mountpoint.

---

### Post by sharks on 2008-05-22
try posting it without quotes or go to the terminal and try it.

---

### Post by lucky.developer on 2008-05-22
yeah.. but i have downloaded many softwares for ubuntu.. which are still there in 7.10,  i want them when i install a fresh copy. i dont want to download all those softwares again for 8.04  help!

---

### Post by lucky.developer on 2008-05-22
lakshman@lakshman-desktop:~$ cd /media/cdrom
lakshman@lakshman-desktop:/media/cdrom$ sudo ./cdromupgrade
[sudo] password for lakshman:
sudo: ./cdromupgrade: command not found
lakshman@lakshman-desktop:/media/cdrom$ 



that was the output i got when i typed those commands

---

### Post by lucky.developer on 2008-05-22
how do i do my 8.04 upgrade from cd correctly...please help

---

### Post by sharks on 2008-05-22
try this now:
press alt+f2

> gksu sh /cdrom/cdromupgrade 

or try it in terminal.

---

### Post by zvacet on 2008-05-22
You **need alternate CD** to do upgrade from disc.Just put CD in drive and you should see message that upgrade to new version is available.If you don´t see that message then

```
gksu "sh /cdrom/cdromupgrade"
```

Never mind how slow your connection is stay connected.At some point it will ask you do you wish upgrade and updates or just upgrade.Choose upgrade without updates.You will update system later.

---

### Post by prshah on 2008-05-22
> **lucky.developer said:**
> lakshman@lakshman-desktop:~$ cd /media/cdrom
lakshman@lakshman-desktop:/media/cdrom$ sudo ./cdromupgrade
[sudo] password for lakshman:
sudo: ./cdromupgrade: command not found


OK, try instead```

sudo sh cdromupgrade
```

---

