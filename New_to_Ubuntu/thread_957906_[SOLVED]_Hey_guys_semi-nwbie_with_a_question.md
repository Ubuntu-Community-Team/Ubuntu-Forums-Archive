---
title: "[SOLVED] Hey guys semi-nwbie with a question"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Sheeplauncher on 2008-10-24
Hey guys i'm a recent linux convert from XP. Anyways i just had it preinstalled on my dell laptop. After a few days i had some driver issues. If i enable it i can only run in 800 x 600 and it prompts me to find my driver and i have tried all of them but none work. It works fine without the driver but then i cannot use games or other stuff via wine. Dell is essentially useless of course and was wondering if you guys had any suggestions. 

Thanks

---

### Post by eternalnewbee on 2008-10-24
Go to Main Menu > System > Aministration > Hardware Drivers, and see if there are any drivers enabled.

---

### Post by eternalnewbee on 2008-10-24
Any progress?...

---

### Post by Sheeplauncher on 2008-10-24
There is a driver installed sorry if i ddint calrify btu when i boot up with it enabled it prompts me saying ubuntu needs to run in low graphics mode then gives me a config option for which driver i want to use and none i tried work. when i disbale it works for some reason just can't play games etc

---

### Post by eternalnewbee on 2008-10-24
What kind of graphic Card do you have? Is it onboard, Nvidia, ATI?

---

### Post by Sheeplauncher on 2008-10-24
should be onboard nvidia since this is a laptop

---

### Post by eternalnewbee on 2008-10-24
Yes. that's logical. Have you tried to change the resolution in Main Menu > System > Preferences > Screen Resolution?

---

### Post by Sheeplauncher on 2008-10-24
yes only lets me go to 800x 600 but with it disabled up to 1280 x 1050 or w/e it is

---

### Post by eternalnewbee on 2008-10-24
I can't help you any further ( limited knowledge ), but I know there are some commands to update your driver. You'll have to be patient for answers from more experienced users, and in the mean time search in the Forums for similar problems related to yours.
I'll do a search myself and see what I can come up with...

---

### Post by Sheeplauncher on 2008-10-24
alright cool i will ina few

---

### Post by eternalnewbee on 2008-10-24
OK. You need to start by mentioning your system specs. For example mine:
________________________________________
Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by eternalnewbee on 2008-10-24
Other examples can be found here:
[http://ubuntuforums.org/showthread.php?t=566529&highlight=resolution](http://ubuntuforums.org/showthread.php?t=566529&highlight=resolution)

---

### Post by floyd-humphrey on 2008-10-24
Hello,
I don't know if this directly matters here, it was quite a while ago, but I had two computers jumping suddenly to 800x600. What I had to do was manually editing the x-server configuration file (xorg.conf, of course as super-user). Since then it never happened again, even with new installations, might have been the old distro.

I recommend to re-search the settings in the x-server configuration file. This page might help. It's huge, so search for the term 'xorg':

[http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/)

I hope this helps...

---

### Post by eternalnewbee on 2008-10-24
Thanks Floyd, for helping out.
Another link:
[http://ubuntuforums.org/showthread.php?t=771810&highlight=resolution](http://ubuntuforums.org/showthread.php?t=771810&highlight=resolution)

---

### Post by Sheeplauncher on 2008-10-24
gotta head out but ill check after i come back thanks guys

---

### Post by Sheeplauncher on 2008-10-25
Sorry i am still new and tho that seemed helpful it kind of confused me XD I also dont seem to have /etc/x11/xorg.conf. May be the problem

---

### Post by Sheeplauncher on 2008-10-25
[IMG]http://i182.photobucket.com/albums/x119/sheeplauncher/Screenshot.png[/IMG]

What happens in nvidia settings

---

### Post by Sheeplauncher on 2008-10-25
any ideas?

---

### Post by jerome1232 on 2008-10-25
Yup. Try running nvidia-xconfig, install it first (just in case it isn't already then run, then restart x). It should configure xorg correctly.

open up a terminal (system-administration-accessories-terminal)
```
sudo apt-get install nvidia-xconfig
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```

If this totally destroy's graphics and won't let you back in to the gui, this will get the gui back (write this down just in case)

```

# Hit ctrl+alt+F2
# you should be at a text login go ahead and login
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by Sheeplauncher on 2008-10-25
Ok that worked well. But now my nvidia driver no longer is enabled let me check to see if prgms can be run without it or else i may need some other help

---

### Post by Sheeplauncher on 2008-10-25
i can load grpahic intensive programs like starcraft or another game but my drievr isnt enabled so it lags some but if i enable my driver it wants to install something and im afraid that might undo the fix.

---

### Post by jerome1232 on 2008-10-25
nvidia-xconfig should have put the driver in use, the second step should have only been done if you got tossed back into low graphics mode or whatever. Open nvidia settings what does it report as the driver.

---

### Post by Sheeplauncher on 2008-10-25
ok i do sudo nvidia-settings get the same msg i screenshotted before. I did the second step because i lost my gui. My resolution is fixed but graphics still not really work. On the hardware test i dont see the static / bars

---

### Post by jerome1232 on 2008-10-25
ok, another thing to try envy works great for alot people, so lets make sure those previous drivers are gone and try that. Just go through the screens and reboot when it prompts you, you already know how to get your gui back in case disaster strikes.

```
sudo apt-get remove nvidia-glx*
# now reboot
sudo apt-get install envyng-gtk
sudo envyng -g
```


edit: if envyng -g doesn't work, try it as 'sudo envyng -t' for a text based installer.

edit: Yeah generally 'gksu' is used to launch graphical apps as root while 'sudo' is for commandline apps, envyng didn't get along with gksu so I edited it.

---

### Post by Sheeplauncher on 2008-10-25
Ok it pops up.. lets see if this works.

---

### Post by Sheeplauncher on 2008-10-25
SUCCESS!!!! woot resolution restored and games dont lag! that did the trick I am in your debt thanks a lot

---

### Post by jerome1232 on 2008-10-25
/cheer

And just as an fyi (I was reading over some of the thread) When you tried to edit xorg it failed because Linux is actually case sensitve, so capital X is not lowercase x.

Not that you need to edit it now this is just for future reference or whatever.

The path to xorg.conf is:

/etc/**X**11/xorg.conf

Glad we could get it fixed don't forget to mark the thread as solved (so other's don't try to help what's been fixed and so that other's know a solution can be found here) Just click thread tools in the upper right and mark it as solved.

---

