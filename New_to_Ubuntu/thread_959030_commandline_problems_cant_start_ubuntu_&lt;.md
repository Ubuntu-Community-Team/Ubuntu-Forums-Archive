---
title: "commandline problems? cant start ubuntu :&lt;"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by zuttoh on 2008-10-26
yeah so this forum name was totally matching for me.. ;) 

so my problem is that i cant "start" the pc.. it always goes to commandline.. if i press esc i get the list and in that list is just halt, reboot and few others what wont do anything to me..

i have windows installed on this and i tried to go on "safe mode" cause of my pc is raped totally and it didnt connect with myt wireless to net [yes i did got ubuntu up once ;)] after i rebooted again it started just opening that commandline..

some tips? did i explain clearly enough?

Regarding, zuttoh who fails at failing.

---

### Post by NewJack on 2008-10-26
If you are in command line in Ubuntu, type the following:

```
startx
```

That should get you started.  If not there may be a problem with the way your xorg.conf is setup with your hardware.  I remember having an issue with my Nvidia card when I first installed Dapper and getting sent to the command line.  From the command line, type the following:

```
sudo nano /etc/X11/xorg.conf 			 		
```

This will open the command line text editor nano and you can edit your xorg.conf file.  

Hope this helps you.

P.S.-  For future reference, make sure you give as many specs as you can for your computer since most problems like this are usually hardware related.  No worries.

---

### Post by zuttoh on 2008-10-26
> **NewJack said:**
> If you are in command line in Ubuntu, type the following:

```
startx
```

That should get you started.  If not there may be a problem with the way your xorg.conf is setup with your hardware.  I remember having an issue with my Nvidia card when I first installed Dapper and getting sent to the command line.  From the command line, type the following:

```
sudo nano /etc/X11/xorg.conf 			 		
```

This will open the command line text editor nano and you can edit your xorg.conf file.  

Hope this helps you.

P.S.-  For future reference, make sure you give as many specs as you can for your computer since most problems like this are usually hardware related.  No worries.

thank you! i try that.. hopefully works ;)

---

