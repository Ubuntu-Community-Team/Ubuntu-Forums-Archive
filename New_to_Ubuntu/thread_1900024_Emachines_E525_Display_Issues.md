---
title: "Emachines E525 Display Issues"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by Hubok on 2011-12-25
Hello everyone, I am using an Emachines E525 Laptop that I bricked Windows 7 on. I installed Ubuntu 11.10, but the backlight for the display would not work. I later installed 10.04 LTS and went to try to find a solution.

Is there an easy way to fix this? A Terminal command?

P.S. Backlight control doesn't work on 10.04 LTS apparently.

---

### Post by Hubok on 2011-12-25
Bump!

---

### Post by Hubok on 2011-12-25
Another bump?

---

### Post by Mark Phelps on 2011-12-26
First of all, quit bumping-- that will not get you a response sooner.

Second, backlight is hardware.  IF it's not working at all, there's nothing you can do in software to MAKE it work.

---

### Post by jsebean on 2011-12-27
> **Mark Phelps said:**
> First of all, quit bumping-- that will not get you a response sooner.

Second, backlight is hardware.  IF it's not working at all, there's nothing you can do in software to MAKE it work.

That is an ignorant reply first of all you couldn't lighten up could you buddy? Instead of rudely telling to stop bumping say it nicely, it makes the world a better place. How do you expect people want to use Ubuntu when they get responses like that.

On top of that, your suggestion (telling) is wrong. I have the same exact problem, and obviously this persons backlight DOES work because it works for then in 10.04 :P. I had a solution to the problem bit it is a bug in Ubuntu which has been reported here. It is not a hardware issue.

What I will say to Hubok,
There was a solution posted on the forums I used once in Ubuntu 11.04 (when the problem started) and once I find it I will post it here for you.

---

### Post by jsebean on 2011-12-27
Unlike previous replies, this is a useful one that will solve the issue :D.
The solution to this bug.

Until this bug is fixed, here is how to fix the backlight issue that works for most users.

First of all, one problem some have is when they boot the OS after installed there's no backlight, and sometimes there's no backlight in the installer either. To get the backlight to come on so you can install Ubuntu, do this:

1. Insert your Ubuntu install disc (or usb drive) and reboot.
2. When you boot the disc or usb drive and you see the "Purple Ubuntu screen" or Ubuntu splash, right away, hold the Fn button and dim your screen brightness then brighten it back up. If you forget to do this and the splash (or purple screen) is gone then the backlight probably wont work and you can't install Ubuntu.

Once ubuntu is installed and you boot from the HDD, do the same when you boot Ubuntu. When you see the purple screen, right away Hold Fn button and dim the screen down and up. Most emachines, being made by acer, to do this, hold Fn button and then hit the left arrow key then the right arrow key.

By doing this, Ubuntu will boot with the backlight. I don't know why, but it does.

Now, that's a bit annoying to fix, and once Ubuntu is booted, you can't adjust your backlight.  What we want to do is make ubuntu turn the backlight on automatically when you boot it and also, allow you to adjust your backlight once Ubuntu is booted. To do this:

Open terminal.
Type in:
```
gksudo gedit /etc/rc.local
```
and hit enter.

Find:
```
exit 0
```

Above exit 0, put in:
```
setpci -s 00:02.0 F4.B=00
```

Save the file, and exit Gedit. If you get a popup message the "untitled document" isn't save, ignore it and close without saving.

This fix will automatically make the backlight turn on upon boot.

Now to ensure you can adjust your backlight once Ubuntu has booted:
In terminal, enter the command:
```
gksudo gedit /etc/default/grub
```

In the file, find the line:
```
GRUB_CMDLINE_LINUX=""
```

Change that line to:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```

Save the file. Exit gedit. If prompted to save untitled document, don't, choose close without saving.

Now in terminal, type the command:
```
sudo update-grub
```

Wait for the process to finish then exit terminal. Reboot your PC.

Once rebooted, you will notice the purple screen, but you don't need to adjust your backlight this time. You'll notice once you pass the boot purple screen, the backlight will go out. Don't worry. Wait a few seconds, then the backlight will come on, and ubuntu will boot up and you'll hear the Ubuntu startup sound.

You will also notice that now you can also use the Fn key and use the right and arrow keys to adjust the brightness. (Or whatever keys you use to adjust the brightness). YAY! It's fixed. :P


A couple of things to consider:
For some users, the backlight still won't automatically turn on. You can however use the brightness controls after Ubuntu is booted to turn the backlight on. If the backlight after doing these fixes still wont turn on, go back to this command and run it "gksudo gedit /etc/rc.local", find the line "setpci -s 00:02.0 F4.B=00" and change it to "setpci -s 00:02.0 F4.B=FF". (without quotes of course). Save and reboot.
Also, you'll notice if you go into standby (and I think Hibernate as well), the backlight will probably be off. I'm not aware of a way to fix this but to get the backlight back on use the Fn key and adjust your backlight to get it back on.
For some users, you may also notice that the backlight adjust keys are backwards. Mine aren't, but some users' are. I am not aware of a way to fix this but it's not that big of a bug. So adjust your backlight use the dim button to brighten the screen and the brighten button to dim the screen :P.

If you have any questions, I'll try to remember to keep an eye on this topic so I can do any further assistance. 

It's a really annoying bug and a bug report is filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438)

Hope this helps :D
-Jonah

---

### Post by Hubok on 2011-12-28
> **jsebean said:**
> Unlike previous replies, this is a useful one that will solve the issue :D.
The solution to this bug.

Until this bug is fixed, here is how to fix the backlight issue that works for most users.

First of all, one problem some have is when they boot the OS after installed there's no backlight, and sometimes there's no backlight in the installer either. To get the backlight to come on so you can install Ubuntu, do this:

1. Insert your Ubuntu install disc (or usb drive) and reboot.
2. When you boot the disc or usb drive and you see the "Purple Ubuntu screen" or Ubuntu splash, right away, hold the Fn button and dim your screen brightness then brighten it back up. If you forget to do this and the splash (or purple screen) is gone then the backlight probably wont work and you can't install Ubuntu.

Once ubuntu is installed and you boot from the HDD, do the same when you boot Ubuntu. When you see the purple screen, right away Hold Fn button and dim the screen down and up. Most emachines, being made by acer, to do this, hold Fn button and then hit the left arrow key then the right arrow key.

By doing this, Ubuntu will boot with the backlight. I don't know why, but it does.

Now, that's a bit annoying to fix, and once Ubuntu is booted, you can't adjust your backlight.  What we want to do is make ubuntu turn the backlight on automatically when you boot it and also, allow you to adjust your backlight once Ubuntu is booted. To do this:

Open terminal.
Type in:
```
gksudo gedit /etc/rc.local
```and hit enter.

Find:
```
exit 0
```Above exit 0, put in:
```
setpci -s 00:02.0 F4.B=00
```Save the file, and exit Gedit. If you get a popup message the "untitled document" isn't save, ignore it and close without saving.

This fix will automatically make the backlight turn on upon boot.

Now to ensure you can adjust your backlight once Ubuntu has booted:
In terminal, enter the command:
```
gksudo gedit /etc/default/grub
```In the file, find the line:
```
GRUB_CMDLINE_LINUX=""
```Change that line to:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```Save the file. Exit gedit. If prompted to save untitled document, don't, choose close without saving.

Now in terminal, type the command:
```
sudo update-grub
```Wait for the process to finish then exit terminal. Reboot your PC.

Once rebooted, you will notice the purple screen, but you don't need to adjust your backlight this time. You'll notice once you pass the boot purple screen, the backlight will go out. Don't worry. Wait a few seconds, then the backlight will come on, and ubuntu will boot up and you'll hear the Ubuntu startup sound.

You will also notice that now you can also use the Fn key and use the right and arrow keys to adjust the brightness. (Or whatever keys you use to adjust the brightness). YAY! It's fixed. :P


A couple of things to consider:
For some users, the backlight still won't automatically turn on. You can however use the brightness controls after Ubuntu is booted to turn the backlight on. If the backlight after doing these fixes still wont turn on, go back to this command and run it "gksudo gedit /etc/rc.local", find the line "setpci -s 00:02.0 F4.B=00" and change it to "setpci -s 00:02.0 F4.B=FF". (without quotes of course). Save and reboot.
Also, you'll notice if you go into standby (and I think Hibernate as well), the backlight will probably be off. I'm not aware of a way to fix this but to get the backlight back on use the Fn key and adjust your backlight to get it back on.
For some users, you may also notice that the backlight adjust keys are backwards. Mine aren't, but some users' are. I am not aware of a way to fix this but it's not that big of a bug. So adjust your backlight use the dim button to brighten the screen and the brighten button to dim the screen :P.

If you have any questions, I'll try to remember to keep an eye on this topic so I can do any further assistance. 

It's a really annoying bug and a bug report is filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438)

Hope this helps :D
-Jonah

Thanks for telling me the fix, I'll try it tomorrow once I can start burning the new disc.

(Can't wait!)

---

### Post by anewguy on 2011-12-28
Please do note, however, that Mark is correct -> the forum rules say no bumping before 24 hours have elapsed.  So please, in the future, wait 24 hours before bumping.  You see, EVERYONE who posts with a problem here thinks their problem is the most important and must be fixed NOW.  For people who demand that type of service there is paid support.  This is a volunteer forum, and no one persons problem is of any higher importance than the next.

So, if you're problem is solved, great.  Just remember the forum rules - if you haven't read them, you'd be strongly advised to do so.

---

### Post by ajit.patell on 2012-01-04
[U][B]
Ubuntu Blacklight fixes ACER FIXES



Create an autostartup script for Debian and Ubuntu systems


In Debian-based distributions (and here I’m also talking about the widely-spread Ubuntu), there is no rc.local file preinstalled. The good thing is that you can make one easily so you can have a place to put commands to be started up automatically at boot. Here’s what you have to do:

sudo nano /etc/init.d/local.autostart

You can name the new file whatever you want, but in this example we’ll use local.autostart. Paste
=====================================================================================================

#!/bin/sh

sudo setpci -s 00:02.0 F4.B=0


================================================================================================

CTRL+O TO WRITE FILE PRESS ENTER
CTRL TO EXIT
=======================================================

on the first line of the file and your command(s) underneath, one after the other. Now save and close and make the file executable with

sudo chmod +x /etc/init.d/local.autostart

Make the file be recognized as an init script:

sudo update-rc.d local.autostart defaults 80

Now, every time you boot up your Debian-based distribution, the commands you set in /etc/init.d/local.autostart will “magically” autostart.
[/B][/U]

---

### Post by digitalmouse on 2012-01-08
> **anewguy said:**
> Please do note, however, that Mark is correct -> the forum rules say no bumping before 24 hours have elapsed. 

first bump by original poster was "2 weeks ago".  second bump was "1 week ago" (both according to the text under the user's name in each post sidebar).  i may be wrong, but i'm pretty sure the time between 2 weeks ago and 1 week ago is longer than 24 hours!

:p

regardless, thanks to jsebean for the info!

---

### Post by casondave on 2012-01-30
HEY !   Thanks to jsebean .... tried the Fn down/up thing on the login screen and it worked !
 
Still can't get the brightness to behave but I also noticed that when I go thru all the settings from blank to bright it seems to go from dark to bright and back to darker .... odd.
 
Can't get the setpci command to work anymore either but this helps!  It's the intel driver at 00.02.0 but thanks again!
 
Cheers'
Dave

---

### Post by EngineersGarage on 2012-04-30
I have the E725...

Had same problem.. Fixed in simmilar way..

Had a fix for hibernation...but couldnt find one for sleep...

Im looking for that fix now after I upgraded. just cant seem to find it. will let you know when i do.

Will.

---

### Post by jsebean on 2012-07-07
> **EngineersGarage said:**
> I have the E725...

Had same problem.. Fixed in simmilar way..

Had a fix for hibernation...but couldnt find one for sleep...

Im looking for that fix now after I upgraded. just cant seem to find it. will let you know when i do.

Will.
thats the exact model I have, E725. The fix I posted works perfectly for me. Standby works and Hibernate was taken out IIRC, though I use KDE anyway and it works there.

The only problem with restoring from sleep, is I have to adjust the backlight up and down a couple times with the FN+Right/Left keys to get it to come back on when I come out of standby.

---

### Post by Scott1980 on 2012-12-01
> **jsebean said:**
> Unlike previous replies, this is a useful one that will solve the issue :D.
The solution to this bug.

Until this bug is fixed, here is how to fix the backlight issue that works for most users.

First of all, one problem some have is when they boot the OS after installed there's no backlight, and sometimes there's no backlight in the installer either. To get the backlight to come on so you can install Ubuntu, do this:

1. Insert your Ubuntu install disc (or usb drive) and reboot.
2. When you boot the disc or usb drive and you see the "Purple Ubuntu screen" or Ubuntu splash, right away, hold the Fn button and dim your screen brightness then brighten it back up. If you forget to do this and the splash (or purple screen) is gone then the backlight probably wont work and you can't install Ubuntu.

Once ubuntu is installed and you boot from the HDD, do the same when you boot Ubuntu. When you see the purple screen, right away Hold Fn button and dim the screen down and up. Most emachines, being made by acer, to do this, hold Fn button and then hit the left arrow key then the right arrow key.

By doing this, Ubuntu will boot with the backlight. I don't know why, but it does.

Now, that's a bit annoying to fix, and once Ubuntu is booted, you can't adjust your backlight.  What we want to do is make ubuntu turn the backlight on automatically when you boot it and also, allow you to adjust your backlight once Ubuntu is booted. To do this:

Open terminal.
Type in:
```
gksudo gedit /etc/rc.local
```and hit enter.

Find:
```
exit 0
```Above exit 0, put in:
```
setpci -s 00:02.0 F4.B=00
```Save the file, and exit Gedit. If you get a popup message the "untitled document" isn't save, ignore it and close without saving.

This fix will automatically make the backlight turn on upon boot.

Now to ensure you can adjust your backlight once Ubuntu has booted:
In terminal, enter the command:
```
gksudo gedit /etc/default/grub
```In the file, find the line:
```
GRUB_CMDLINE_LINUX=""
```Change that line to:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```Save the file. Exit gedit. If prompted to save untitled document, don't, choose close without saving.

Now in terminal, type the command:
```
sudo update-grub
```Wait for the process to finish then exit terminal. Reboot your PC.

Once rebooted, you will notice the purple screen, but you don't need to adjust your backlight this time. You'll notice once you pass the boot purple screen, the backlight will go out. Don't worry. Wait a few seconds, then the backlight will come on, and ubuntu will boot up and you'll hear the Ubuntu startup sound.

You will also notice that now you can also use the Fn key and use the right and arrow keys to adjust the brightness. (Or whatever keys you use to adjust the brightness). YAY! It's fixed. :P


A couple of things to consider:
For some users, the backlight still won't automatically turn on. You can however use the brightness controls after Ubuntu is booted to turn the backlight on. If the backlight after doing these fixes still wont turn on, go back to this command and run it "gksudo gedit /etc/rc.local", find the line "setpci -s 00:02.0 F4.B=00" and change it to "setpci -s 00:02.0 F4.B=FF". (without quotes of course). Save and reboot.
Also, you'll notice if you go into standby (and I think Hibernate as well), the backlight will probably be off. I'm not aware of a way to fix this but to get the backlight back on use the Fn key and adjust your backlight to get it back on.
For some users, you may also notice that the backlight adjust keys are backwards. Mine aren't, but some users' are. I am not aware of a way to fix this but it's not that big of a bug. So adjust your backlight use the dim button to brighten the screen and the brighten button to dim the screen :P.

If you have any questions, I'll try to remember to keep an eye on this topic so I can do any further assistance. 

It's a really annoying bug and a bug report is filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438)

Hope this helps :D
-Jonah


JUST WANT TO VERIFY THAT ( after many hours research) THIS METHOD WORKED FOR ME!!!!   


Thanks :)

---

### Post by jsebean on 2012-12-02
Awesome, glad it worked. I always come back and look at this every time I format my PC lol. I really wish they kernel guys would fix this issue soon, it is mega annoying, and still exists as of 12.10. If I were smarter and knew the extreme geek talk I would bump the bug report lol.

---

### Post by Palaine on 2013-01-05
Thanks! I'm new to Linux, I used Lucid, and I naively thought if I'm not installing, but updating 12.04, it will be fine. Well, it wasn't. It was a fresh installation, but I had some files which I didn't wanna loose. But your solution just worked perfectly! :D:D God bless you!

---

