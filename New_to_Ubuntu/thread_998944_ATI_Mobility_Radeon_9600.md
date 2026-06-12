---
title: "ATI Mobility Radeon 9600"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Tinystickfigure on 2008-12-01
Hello, I am an absolute beginner with Ubuntu and I loaded Ubuntu 8.10 onto my HP Pavilion zx5000 and it will only run in low graphics mode (800x600). I downloaded the ati 8.11 drivers installers off the website, but it is a .run file and i dont know how to get it to execute. Any help would be much appreciated.

---

### Post by halitech on 2008-12-01
open a terminal and navigate to where you downloaded the file

then run```
sudo sh ./ati-driver-installer-8-10-x86.x86_64.run
``` and follow the prompts

---

### Post by Tinystickfigure on 2008-12-01
sorry, it is on my desktop, how do i navigate to there?

---

### Post by Bablefish on 2008-12-01
actually it's this command in Terminal  $ cd ~/Desktop

But a bit of warning about installing those ATI drivers. You have an equal chance they will work as you have of crashing your video drivers. I know the latter is what happened to me. All I can suggest if it does happen and they crash. Reinstall your OS, it's a hell of a lot easier.

---

### Post by halitech on 2008-12-01
if it crashes and they can get to a command prompt, they can run ```
xfix
```and it should fix up the drivers.

---

### Post by Tinystickfigure on 2008-12-01
ok so one more question: i ran it, and it pops up with this ATI proprietary linux driver 8.552 setup window, but the window is too big for the screen and it wont let me move forward, i tried resizing it, but it wont let me move the window beyond the threshold of the top, any insight on how to get around it?

---

### Post by Tinystickfigure on 2008-12-01
wait, sorry, nevermind i got it hahah

---

### Post by Tinystickfigure on 2008-12-01
ok so i installed it and it said successful, and i restarted it and it still goes into low graphics mode. did i miss a step or is there something else i should do?

---

### Post by halitech on 2008-12-01
open a terminal and run```
sudo xfix
``` and see if that sets the correct resolutions.

---

### Post by Tinystickfigure on 2008-12-01
when i run that i get:

sam@sam-laptop:~$ sudo xfix
sudo: xfix: command not found

---

### Post by Tom--d on 2008-12-01
All you need to do is go to System > Admin > Hardware Drivers and enable the ATI driver.

Done.

---

### Post by Tinystickfigure on 2008-12-01
the drivers do not show up under 'hardware drivers' for some reason

---

### Post by Tinystickfigure on 2008-12-01
is there any way for me to go back to 8.06 without losing all my stuff? this is incredibly frustrating...

---

### Post by whitethorn on 2008-12-01
I also have a ATI Mobility 9600.  I didn't try any other drivers when I installed Intrepid and it works perfectly.  I can even watch vidoes with compiz enabled, which wasn't possible before even with the latest ATI drivers.  If you want to try it out, you'll have to empty your xorg.conf to let ubuntu choose a driver for you.  It won't show up in hardware drivers, but everything will work. First backup your old xorg

[code]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksu gedit /etc/X11/xorg.conf[code]

and now just get delete everything and save it.  then reboot

If it doesn't work, then just mv the backup.

---

### Post by superigel1987 on 2009-01-24
hi,
i also looked up for a 3D accelerration driver for my ati radeon 9600 mobility.
but i found anything. is it possible that there is no support for ubuntu 8.10
iam sorry iam a newby in ubuntu (linux).
also used the xorg driver but it also crash in low grafic.
thanks

---

### Post by Punisher660 on 2009-02-02
I am also having the same problems. I did a fresh install of 8.10 on a Dell Inspiron 8600 with the ATI Radeon 9600 Pro Turbo. When I did the original install, everything worked, but it was slow - 

I didn't see anything listed in the hardware manager. 

I then downloaded the driver from ATI and followed their instructions. It broke completely - 

I then tried Envyng - still broken 

I just finished the steps on this post - still broken

It is currently at the point that on bootup it shows "Running in low graphics mode"

How do I get back to the default drivers?

This is frustrating - any ideas?

---

### Post by monikersupreme on 2009-02-07
So is the a consensus yet on if the new ATI drivers work for the Mobility Radeon 9600?

I've got an old NC8000 laptop that I was about to kick back to v8.04 in order to be able to get hardware drivers compatible with my Mobility 9600 but if I can stick w. v8.10 it will be a lot less trouble for me...

I don't get the option of any hardware drivers when I select System->Administration->Hardware Drivers ... 

do I need to download the new ATI drivers separately?

Thanks!

---

