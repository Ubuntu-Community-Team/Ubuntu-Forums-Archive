---
title: "Installing Nvidia Drivers...need help"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-05-11
How do I exit the X server so i can install my nvidia drivers???? Im doing this this way because i tried the enable way and i dont knwo if its working correctly..games are lagging...so just as a fail safe.

I tried this code from a other post....

dtrot@Ubuntu-Dtrot:~$ /etc/init.d/gdm stop
open: Permission denied
 * Stopping GNOME Display Manager...                                            
open: Permission denied
                                                                         [ OK ]
dtrot@Ubuntu-Dtrot:~$ 

Tried installing the drivers and still says im in a x server.....any idea?

Thanks!

---

### Post by cprofitt on 2008-05-11
> **dtrot55 said:**
> How do I exit the X server so i can install my nvidia drivers???? Im doing this this way because i tried the enable way and i dont knwo if its working correctly..games are lagging...so just as a fail safe.

I tried this code from a other post....

dtrot@Ubuntu-Dtrot:~$ /etc/init.d/gdm stop
open: Permission denied
 * Stopping GNOME Display Manager...                                            
open: Permission denied
                                                                         [ OK ]
dtrot@Ubuntu-Dtrot:~$ 

Tried installing the drivers and still says im in a x server.....any idea?

Thanks!

Is there a reason you want to install manually vs. using the restricted drivers?

If you were unaware of the restricted drivers just go to System | Administration | Hardware drivers and the pop-up will show you the drivers that are available from the repositories.

---

### Post by dtrot55 on 2008-05-11
I enabled the nvidia drivers already through the hardware manager....but was getting very poor response from WINE and also the Desktop effects weren't that great either....in one of my other post someone suggested i do it manually...which i can do ...right now im stuck at a blue screen saying i need to use the "runlevel 3 ('telinit 3') before installing????? any idea how to do that?

---

### Post by subzero316 on 2008-05-11
> **dtrot55 said:**
> How do I exit the X server so i can install my nvidia drivers???? Im doing this this way because i tried the enable way and i dont knwo if its working correctly..games are lagging...so just as a fail safe.

I tried this code from a other post....

dtrot@Ubuntu-Dtrot:~$ /etc/init.d/gdm stop
open: Permission denied
 * Stopping GNOME Display Manager...                                            
open: Permission denied
                                                                         [ OK ]
dtrot@Ubuntu-Dtrot:~$ 

Tried installing the drivers and still says im in a x server.....any idea?

Thanks!





First press
CTRL+ALT+F1 you will enter the console mode.
Then
```
sudo /etc/init.d/gdm stop
```

Then try installing the drivers 
I suggest you install ENVY.

---

### Post by dtrot55 on 2008-05-11
I got the nvidia drivers installed....and i tried envy before i got 8.04 and it always conflicted with my sound drivers for some reason.... 

************************
HOW I SOLVED IT FOR YOU NOOBS LIKE ME!
************************

rebooted into safe mode

Code:
sudo telinit 3

Sudo /etc/init.d/gdm stop

PATH TO YOUR NVIDIA PKG

EX: 
cd /home/dtrot/Desktop
sudo sh Nvidia-Linux-x86-169.12-pkg1.run

Sudo reboot

---

### Post by dreadlord_chris on 2008-05-12
When you say "rebooted into safe mode", are you refering to the "Recovery" option on the Grub menu? If so then you were (are) already logged in as **root**, so none of the sudo's were necessary. Also, *for your purposes*, _telinit 3_ and _/etc/init.d/gdm stop_ both accomplish the same thing - shutting down the display manager (which shouldn't be running anyway, if you're in Recovery Mode), so there's no reason to use both.

---

