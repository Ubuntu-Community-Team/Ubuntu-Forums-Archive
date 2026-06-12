---
title: "Need help with nvclock"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Christopher on 2008-11-05
Im looking at downloading this program here  [http://www.linuxjournal.com/content/adjust-fan-speed-you-nvida-graphics-card](http://www.linuxjournal.com/content/adjust-fan-speed-you-nvida-graphics-card)   But im not sure what to download when I click on the link to get the file  here [http://nvclock.cvs.sourceforge.net/viewvc/nvclock/nvclock/](http://nvclock.cvs.sourceforge.net/viewvc/nvclock/nvclock/)  


Can someone help with the install of this? Thank you in advance.

---

### Post by taurus on 2008-11-05
This is the link you want to use to download the source and build it yourself.

[http://sourceforge.net/project/showfiles.php?group_id=21335&package_id=177733&release_id=565905](http://sourceforge.net/project/showfiles.php?group_id=21335&package_id=177733&release_id=565905)

Remember, you need to install the build-essential and checkinstall packages first before you can build anything from source.

---

### Post by Christopher on 2008-11-05
> **taurus said:**
> Remember, you need to install the build-essential and checkinstall packages first before you can build anything from source.

Whats the command for the install of those packages? Thank you in advance for all of your help.

---

### Post by tuxxy on 2008-11-05
Why not install nvclock from the repos? 

```
sudo apt-get install nvclock
```

---

### Post by Christopher on 2008-11-05
> **tuxxy said:**
> Why not install nvclock from the repos? 

```
sudo apt-get install nvclock
```

SWEET!  thank you very much,

---

### Post by wizard10000 on 2008-11-05
> **tuxxy said:**
> Why not install nvclock from the repos? 

```
sudo apt-get install nvclock
```

and nvclock-gtk, which is the graphical version.  If you want something that starts when X does you can use the settings from nvclock-gtk to add to your X session.  You can't use my settings, but I just added 

nvclock -n 400 -m 650

to my X session.

---

### Post by Christopher on 2008-11-05
> **wizard10000 said:**
> and nvclock-gtk, which is the graphical version.  If you want something that starts when X does you can use the settings from nvclock-gtk to add to your X session.  You can't use my settings, but I just added 

nvclock -n 400 -m 650

to my X session.


Awsome thank you everyone!   :mrgreen:

---

### Post by thegrilledcheese on 2009-07-31
I'm having a similar problem.  I'd like my fan on my 8800GT to run at 75% everytime I start my computer.  I've done sudo apt-get install nvclock-gtk but now I don't know what else to do.  I don't see the application in my menus.  How do I run the program and how do it set it to make my fan run @ 75% at startup everytime?

Thank you!!

thegrilledcheese

---

### Post by thegrilledcheese on 2009-08-01
Fixed!!  Now able to automatically set nvidia 8800gt fan speed on startup.

I had problems running the GUI.  The install name is nvclock-gtk but the executable is nvclock_gtk.  I ended up removing the GUI version and installed nvclock.  Created a bash script:

```

#! /bin/bash
nvclock -F 85 -f

```Added that script to System>Preferences>Startup Applications.

-F or --fanspeed is disabled by default so needed to add the -f to force the command.

- thegrilledcheese

---

### Post by henryfranz2005 on 2009-10-03
hi, me too I can't see the GUI of this application. Please help! :)

---

### Post by Christopher on 2009-10-04
> **henryfranz2005 said:**
> hi, me too I can't see the GUI of this application. Please help! :)


Im interested in getting it to run at startup as well. Not sure how to or what to do with a bash script. Sorry for being a newbie lol. Maybe someone else could help, do i open gedit and save it?

---

### Post by henryfranz2005 on 2009-10-04
yeah, we need help. :lolflag:

---

### Post by WSmart on 2009-10-22
I tried installing nvclock a couple months ago and couldn't get it to work, nothing but nvclock -h worked.  I got a stack bashing error.  Suddenly it works.  I didn't do anything.  Must have been an update to something.  So cool.  I also got a great deal on my car insurance..... :)

If you want to get this to set automatically, go into System>Preferences>Startup Applications(or sessions with older Ubuntu releases), add a startup application and add your command with a gnome-terminal -x prefix.  

gnome-terminal -x nvclock -n 420 -m 670

Which you know the command, add your own speeds.  You need that 'gnome-terminal -x' to signal a terminal command.   Using ctrl-alt-backspace to reset the x server is very handy for setting up startup application, though I think it's been disabled with newer Ubuntu version-you'd have to add that, or I think you can just log out via the menu, rather then a complete system reboot, to test.  

I'm just happy my nvclock is working, so not in a hurry to try the gui, @grilledcheese.   If you post more details somebody might help, but you'd have better luck starting a new post, I bet.  If simply sudo apt-get install nvclock-gtk and running nvclock_gtk from the command line does not work, I don't know.  And that's in gnome.  Not sure about KDE or XFCE, Kubuntu or Xubuntu.  The command line is very easy to use with this program, however.  Just pull up the help, nvclock -h .

Thanks all,  

Be real, be sober.

---

### Post by Christopher on 2009-10-25
> **WSmart said:**
> I tried installing nvclock a couple months ago and couldn't get it to work, nothing but nvclock -h worked.  I got a stack bashing error.  Suddenly it works.  I didn't do anything.  Must have been an update to something.  So cool.  I also got a great deal on my car insurance..... :)

If you want to get this to set automatically, go into System>Preferences>Startup Applications(or sessions with older Ubuntu releases), add a startup application and add your command with a gnome-terminal -x prefix.  

gnome-terminal -x nvclock -n 420 -m 670

Which you know the command, add your own speeds.  You need that 'gnome-terminal -x' to signal a terminal command.   Using ctrl-alt-backspace to reset the x server is very handy for setting up startup application, though I think it's been disabled with newer Ubuntu version-you'd have to add that, or I think you can just log out via the menu, rather then a complete system reboot, to test.  

I'm just happy my nvclock is working, so not in a hurry to try the gui, @grilledcheese.   If you post more details somebody might help, but you'd have better luck starting a new post, I bet.  If simply sudo apt-get install nvclock-gtk and running nvclock_gtk from the command line does not work, I don't know.  And that's in gnome.  Not sure about KDE or XFCE, Kubuntu or Xubuntu.  The command line is very easy to use with this program, however.  Just pull up the help, nvclock -h .

Thanks all,  

Be real, be sober.


I just want to set my fan speed at 100% & i want it to bootup at 100%, Ok i'll give it a try. thank you.

---

