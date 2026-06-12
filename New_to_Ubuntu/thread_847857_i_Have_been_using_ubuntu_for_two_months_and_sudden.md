---
title: "i Have been using ubuntu for two months and suddenly there is a problem with xserver?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by ledzeppelin on 2008-07-02
I get the error message (exactly written with the way it was seen including spacing):
Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when the problem is corrected.

---

### Post by Bubba64 on 2008-07-03
Did you get this on a startup, and did you try a restart to see if it fixes this problem. Once in awhile you can get a X failure, usually mine are associated with a force quit.

---

### Post by ledzeppelin on 2008-07-03
got it at startup, rebooting doesnt fix

---

### Post by Sinkingships7 on 2008-07-03
Press ESC at grub, boot into recovery mode, and run the command:
```
fsck
```

---

### Post by ledzeppelin on 2008-07-03
it didnt work

i get 


fsck 1.40.8 (13-Mar-2008)
fsck.ect3: Unable to resolve 'UUID=a93daebb-d7ec-406a-b92c-94d55396f9ff'

that looks a lot like a crack code

---

### Post by rockerphil on 2008-07-03
try reconfiguring your xserver, run this at the command prompt

sudo dpkg-reconfigure xserver-xorg

if that doesn't work, then i'd try selecting the "recovery mode" from GRUB and have it fix the X server

---

### Post by pferpaddy on 2008-07-03
press esc at the bootloader and go to the friendly recovery mode
then go to friendly recovery option and when it loads up the menu go to  repair xserver then resume normal an when your back to gnome reenable ur hardware driver in the restricted driver section
hope that helps

---

### Post by ledzeppelin on 2008-07-03
Doing the sudo code freezes my computer at the window it brings up and doing it from recovery mode tells me a file cannot be opened and it is read only.

---

### Post by ledzeppelin on 2008-07-03
ill be back in some time but please keep on giving me ideas on what to do.

---

### Post by pferpaddy on 2008-07-03
sorry to have to tell you this but its hardware related :(

---

### Post by ledzeppelin on 2008-07-03
you have to be kidding me, my windows won't install and now my ubuntu won't work. I am extremely dissapointed with ubuntu

---

### Post by swisscow on 2008-07-03
> **pferpaddy said:**
> sorry to have to tell you this but its hardware related :(

Possibly not. Could be an update that has broken things, could be the OP did something without realising.

Follow the steps people suggest and search for posts for people with similar problems with your graphics card before you go off to the shops.

---

