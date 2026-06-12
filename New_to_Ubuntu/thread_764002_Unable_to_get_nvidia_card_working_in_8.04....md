---
title: "Unable to get nvidia card working in 8.04..."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by shmoe010 on 2008-04-23
I did a fresh install of 8.04 on a new HDD. The first time I loaded it I managed to get in under "low graphics mode", but after that it just turns black (my monitor says "mode not supported."


I've followed several help threads, but to no avail. I have tried manually editing the /etc/modules and /etc/X11/xorg.conf files, then when that didn't work, I followed another thread's directions and ran nvidia-xconfig. At one point I was able to get it back into low graphics mode to get all the updates I need, and I followed yet another fix by installing Envy, but the installation of the driver doesn't complete, it just crashes.

I'm pretty new to linux, and I'm getting frustrated because it seems so intermittent. As of now I'm able to get as far as the login screen (in the 1280x1024 resolution) but logging in just causes my monitor to go blank and say "mode not supported." If anyone else has had similar issues, or knows of a really good fix for this, please let me know.

System Specs:

DFI LanParty Socket 939
Opteron 165
2x1 GB Crucial Ballistix
2x500 GB HDD
eVGA 7800 GTX graphics card
1 kW PC P&C psu

Thanks in advance for your help!

---

### Post by Ub1476 on 2008-04-23
Did you check for any drivers in System>Administration>Hardware Drivers?

---

### Post by shmoe010 on 2008-04-23
> **Ub1476 said:**
> Did you check for any drivers in System>Administration>Hardware Drivers?

I would if I could get into the OS...

I've been tryin to figure out how to get it back to "low-graphics mode" so i can investigate but I can't seem to find how to do it in 8.04.

---

### Post by thisismalhotra on 2008-04-23
when you get to graphical login screen click on a icon on that page I think bottom left (probably called OPTIONS) and click on sessions and try to go to failsafe gnome and see if that lets you in.

If, not see if there is an option of failsafe terminal/command line session there and try to get into terminal.

Post back and we can give you instructions where to go next..

---

### Post by Ub1476 on 2008-04-23
If you edit xorg.conf and use the vesa "failsafe" driver, and maybe setting a lower resolution, you should be able to log in.

---

### Post by Confuzius on 2008-04-23
Check out EnvyNG
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
I'm pretty sure than envy is in the Repos for HH, and can be used from the command line, just check out the instructions at that site.
EnvyNG helped ease all of my nvidia issues, running dual displays with no problems at all.

---

### Post by thisismalhotra on 2008-04-23
> **Confuzius said:**
> Check out EnvyNG
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
I'm pretty sure than envy is in the Repos for HH, and can be used from the command line, just check out the instructions at that site.
EnvyNG helped ease all of my nvidia issues, running dual displays with no problems at all.

I SECOND THAT I ALWAYS USE ENVY

---

### Post by shmoe010 on 2008-04-23
Okay, I tried the failsafe mode from the login screen and it failed (same thing, where my monitor just goes blank and tells me "NO!" lol

Then I tried running envy from the command line and I get an error: Warning: Unable to open display and it quits.

What did I do??

---

### Post by sowelie on 2008-04-23
Right after the screen goes black, press CTRL + ALT + F1.  This will get you to the console.  Then, log in and run the following command and post the output here.

```
cat /var/log/Xorg.0.log
```

This is the log file for X, it'll have output explaining why the display manager can't start.  Also, what kind of monitor are you using?  It sounds like the refresh rate X is trying to use isn't compatible with your machine.  Are you able to get in with the live CD?

---

### Post by shmoe010 on 2008-04-23
> **sowelie said:**
> Right after the screen goes black, press CTRL + ALT + F1.  This will get you to the console.  Then, log in and run the following command and post the output here.

```
cat /var/log/Xorg.0.log
```

This is the log file for X, it'll have output explaining why the display manager can't start.  Also, what kind of monitor are you using?  It sounds like the refresh rate X is trying to use isn't compatible with your machine.  Are you able to get in with the live CD?

Okay, I did this, and although I'm unable to see all the output (because it's a command prompt at low res) I am able to see this:

(II) NVIDIA(0) Setting mode "800x600"

My monitor is a KDS 19" LCD, native res 1280x1024 if that helps.

---

### Post by sowelie on 2008-04-23
Alright, what I would do then is run this command:

```
nano /var/log/Xorg.0.log
```

Now you can hit CTRL + W and search for (EE).  Errors in the log are prefixed with (EE).  Also, look for warnings (WW).  Paste any errors or warnings.

That monitor should have no trouble running at 800x600 and 60Hz.

---

### Post by thisismalhotra on 2008-04-23
> **shmoe010 said:**
> Okay, I tried the failsafe mode from the login screen and it failed (same thing, where my monitor just goes blank and tells me "NO!" lol

Then I tried running envy from the command line and I get an error: Warning: Unable to open display and it quits.

What did I do??

to run envy from command line you need to use envy in text mode by

```
envy -t
```

**and for hardy you need EnvyNG and I dont know if this command changed with that update but I think it should work read the ENVY website pls.**

This FAQ from envy website might help.. at least helped me when I was doing my gaming rig

[http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)


EDIT: As the FAQ showed the command is

```
sudo envyng -t
```

---

### Post by shmoe010 on 2008-04-23
Okay, I managed to get into the failsafe Xterm session. I ran the gui for Envy, let it do its thing, it completed successfully, and upon reboot I didn't get any impovements.

I did get an "EE" from the conf log.

It reads: (EE) Failed to load module "type1" (module does not exist, 0.)

That seems to be the only error.

---

### Post by forrestcupp on 2008-04-23
Try to boot to the recovery mode, then in the menu, choose 'drop to root'.  Then type:
```
apt-get --purge remove nvidia*
```and just let it uninstall everything that has to do with nvidia.  Then type:
```
exit
```which will get you back to that menu, where you should choose to 'fix X'.  When that's done, choose to resume normal boot process and you should be able to get to your desktop.  When you get to your desktop, try EnvyNG again and see if it works this time.  After it's done, you may have to go to System->Administration->Hardware Drivers and enable the restricted drivers.

---

### Post by shmoe010 on 2008-04-23
> **forrestcupp said:**
> Try to boot to the recovery mode, then in the menu, choose 'drop to root'.  Then type:
```
apt-get --purge remove nvidia*
```and just let it uninstall everything that has to do with nvidia.  Then type:
```
exit
```which will get you back to that menu, where you should choose to 'fix X'.  When that's done, choose to resume normal boot process and you should be able to get to your desktop.  When you get to your desktop, try EnvyNG again and see if it works this time.  After it's done, you may have to go to System->Administration->Hardware Drivers and enable the restricted drivers.

Okay, followed this solution, and everything seemed to go fine until I hit "resume normal boot", at which point I got a series of strange colors all over my screen that seemed to be flashing at me.

A reboot yields the same result.

---

### Post by TheLions on 2008-04-23
try downloading drivers from NVIDIA.com and then press ALT+CTRL+F1 and then open folder containing downloaded drivers and type
```
chmod +x NVIDIA-Linux-xXXXX-YYY.YY-ZZZ.run

``` where XXXX is architecture YYY.YY version and ZZZ package
then type ```
sudo  /etc/init.d/gdm stop
```
then run NVIDIA installer by putting this in```
./NVIDIA-Linux-xXXXX-YYY.YY-ZZZ.run
``` in installer select everything "yes" and type ```
sudo  /etc/init.d/gdm start
```

and this should do the trick!!!

---

### Post by CoffeeDaze on 2008-04-23
You may find some issues with Envy drivers (NVIDIA and 8.04 are not always playing nicely)

I used the Virtual Terminal (CTRL+ALT+F1) to install the latest beta driver from NVIDIA's site and it's working great now.  Hopefully they will get the NVIDIA bugs worked out soon after release.

---

### Post by stchman on 2008-04-23
> **shmoe010 said:**
> I did a fresh install of 8.04 on a new HDD. The first time I loaded it I managed to get in under "low graphics mode", but after that it just turns black (my monitor says "mode not supported."


I've followed several help threads, but to no avail. I have tried manually editing the /etc/modules and /etc/X11/xorg.conf files, then when that didn't work, I followed another thread's directions and ran nvidia-xconfig. At one point I was able to get it back into low graphics mode to get all the updates I need, and I followed yet another fix by installing Envy, but the installation of the driver doesn't complete, it just crashes.

I'm pretty new to linux, and I'm getting frustrated because it seems so intermittent. As of now I'm able to get as far as the login screen (in the 1280x1024 resolution) but logging in just causes my monitor to go blank and say "mode not supported." If anyone else has had similar issues, or knows of a really good fix for this, please let me know.

System Specs:

DFI LanParty Socket 939
Opteron 165
2x1 GB Crucial Ballistix
2x500 GB HDD
eVGA 7800 GTX graphics card
1 kW PC P&C psu

Thanks in advance for your help!

If you are using Hardy it is still beta.  Tomorrow the official release of 8.04 so you may want to reinstall.

The best way to install Nvidia drivers is to use Envy.  FOr Hardy yuou need to use EnvyNG.  I am surprised as the 7xxx nvidia cards are supported via the Restricted Drivers manager.

---

