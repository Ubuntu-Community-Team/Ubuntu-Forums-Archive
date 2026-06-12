---
title: "I haven't a clue..."
date: 2012-01-31
forum: New to Ubuntu
---

### Post by Jones235 on 2012-01-31
Is there anywhere for an absolute newbie with Linux to go and get some help?

---

### Post by penguinsfan16 on 2012-01-31
yea your here! lol.

---

### Post by BlinkinCat on 2012-01-31
Hi,

You could look at what is in my signature for a start -

Guide is written by aysiu, a moderator on the Forums - :)

---

### Post by UltimateCat on 2012-01-31
Lot's of websites and help!

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

[http://help.ubuntu.com/community/Firestarter](http://help.ubuntu.com/community/Firestarter)    (If intrested)

[www.canonical.com/support](www.canonical.com/support)

[www.linuxquestions.org](www.linuxquestions.org)

[http://linuxsurvival.com/](http://linuxsurvival.com/)

[www.linuxjournal.com](www.linuxjournal.com)

Welcome to Linux and good luck to you!

---

### Post by QIII on 2012-01-31
We don't have a clue, either!

Ubuntuguide.org

Ubuntu-manual.org

---

### Post by SAIYANPRINCE on 2012-01-31
right here is the best place!

---

### Post by Jones235 on 2012-01-31
> **SAIYANPRINCE said:**
> right here is the best place!
 
 
Thanks for all of the responses.  I am trying to install Ubuntu 11.1 on an older Dell Inspiron 8000 laptop.  It installs and runs but there are two problems:  1. Ubuntu cannot recognize the ATI display hardware and install the proper drivers.  2.  The Linksys PCMCIA wireless adapter that I have is also not recognized by the OS.  My wired modem works fine...
 
I have searched the web and some of these forums but the solutions that I have read do not seem to work for one reason or another (Mostly because of my unfamiliarity with the Linux file system, command line, and user permissions) and it is a bit overwhelming for a newbie to figure out.
 
Any help with this would be appreciated.:)

---

### Post by grahammechanical on 2012-01-31
Open the Dash (Ubuntu icon on the top left) and type help. Have you tried running the Additional Drivers Utility?

Regards and welcome

---

### Post by Jones235 on 2012-01-31
> **grahammechanical said:**
> Open the Dash (Ubuntu icon on the top left) and type help. Have you tried running the Additional Drivers Utility?
 
Regards and welcome
 
The additional drivers search turns up nothing.  I am supposed to be able to edit a .conf file to fix the video problem but I can never open it to edit it...
see:  [http://ubuntuforums.org/showthread.php?p=11655156#post11655156](http://ubuntuforums.org/showthread.php?p=11655156#post11655156)
 
The wireless card is a total mystery.

---

### Post by oldos2er on 2012-02-01
Use this command ```
gksu gedit /etc/X11/xorg.conf
``` to edit your xorg.conf. You may want to make a backup first ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by Paqman on 2012-02-01
> **oldos2er said:**
> Use this command ```
gksu gedit /etc/X11/xorg.conf
``` to edit your xorg.conf. You may want to make a backup first ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

I don't think there actually is an xorg.conf by default any more, but one will be used if you create it.

---

