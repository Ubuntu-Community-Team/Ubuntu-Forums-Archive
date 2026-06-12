---
title: "video card/monitor settings, Big problems"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by CivicSpoon on 2008-08-28
I'm a complete noob when it comes to Ubuntu & Linux in general.  I'm not very good with the commands, and usually search for things and simply cut and paste into the Terminal.  Before I get to the big issue I've created for myself, I'll try to give some info on my computer.
Ubuntu 8.04 (with a dual boot for Windows XP as well), Dell 4600, GeForce 7600, LG L204WT Widescreen monitor.

Until today I had everything set up and running fine, and then I decided to try and hook up my computer to my TV as a 2nd monitor.  I plugged in the S-video cable and had no luck getting it to work.  Through a search I found this link: 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=893694](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=893694)

I did the "sudo apt-get install nvidia-settings", and it installed.  Next (this is where I'm assuming I made the big mistake), I went to the "Screens and Graphics" settings in the Applications>Other menu.  I clicked the "Graphics Card" tab, clicked on "Driver",  clicked the "Choose Driver by Model", clicked "NVIDIA", and went through and selected the GeForce 7 Series.  I saved the settings and rebooted.

When it began rebooting, I could see the Dell start up screen, as well as the boot page (selection of OS') on my TV.  But when Ubuntu loaded up, all I got was a bunch of vertical orange & yellow lines on my monitor, and a black background with some red dots on my TV.  I rebooted (power button), and unplugged the cable from my TV.  Ubuntu then loaded up with a 800X600 resolution; I usually use 1680X1050, if I remember correctly.  Of course, I was stupid enough to mess with these settings and never saved my previous settings (hopefully lesson learned).

I've tried going to the "Screen and Graphics Preferences" thing, manually choosing my monitor and changing the "GeForce 7 series" to the "NVIDIA" in the "Choose driver by name" selection.  I then click the "Test" button and get a black screen for a few seconds and then a message box saying *"Configuration test failed: Please verify the selected devices and configuration."*

I also tried the "sudo nvidia-settings" command, but I get a long message saying *"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the x server."*  This of course makes no sense to me, being a complete noob.

I now realize I was way over my head thinking I could do this.  If anyone has any ideas or insight about these problems, I would GREATLY appreciate it.

---

### Post by tuxxy on 2008-08-28
You enabled the driver for your card at system > admin > hardware drivers ?

If you didnt then uninstall the driver and try that.

---

### Post by alienexplorers on 2008-08-28
You could also try EnvyNG which can be found in the repositories by searching for envy.  Select envy-gtk and envy-core and load those.  When done open applications>system tools>EnvyNG.  Select to uninstall your driver and then don't reboot, but select automatic driver loading.  Let it load your driver and then reboot.  That should clear up your driver problems.  This may also cause a screen res of 800x600.  If you get that we can work on that later.

---

### Post by Crafty Kisses on 2008-08-28
> **alienexplorers said:**
> You could also try EnvyNG which can be found in the repositories by searching for envy.  Select envy-gtk and envy-core and load those.  When done open applications>system tools>EnvyNG.  Select to uninstall your driver and then don't reboot, but select automatic driver loading.  Let it load your driver and then reboot.  That should clear up your driver problems.  This may also cause a screen res of 800x600.  If you get that we can work on that later.

I'm pretty sure if you select EnvyNG, it will select all the needed dependencies. I wouldn't mind seeing the output of your X.org as well.

---

### Post by Hobo Joe on 2008-08-28
Install Envy(link in my sig) and uninstall your drivers then reinstall. Let Envy configure everything.

Then, reboot, and type in the terminal:

```

sudo nvidia-settings

```

Then go to 'X Server Display Configuration'. From there you can set up both screens properly via your nVidia drivers, rather than via Ubuntu.

---

### Post by CivicSpoon on 2008-08-28
Thank you so much for the help everyone!  That fixed all of the problems I was having.  Even my resolution is back to normal.  A new minor problem has popped up though.  At the login screen, all I can see is a big Ubuntu logo in the right bottom corner of my screen.  I can't even see the box to type in my user name and password.  Not really a huge issue since I can just type them in and hit enter, but it's kind of annoying.  But thanks again everyone, I really appreciate all the help.

---

