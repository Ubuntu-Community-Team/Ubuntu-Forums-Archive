---
title: "The system is running in low-graphics mode after upgrade"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by zmoney2 on 2013-12-23
I've ran the latest updates which took me from 13.04 to 13.10 and after rebooting I get the standard "Unbuntu" screen but then I am getting a window which says "The system is running in low-graphics mode" Your screen, graphics card, and input device settings could not be detected correctly. Tyou will need to configure these yourself.
I'm running a Dell Latitude D620 and it was working fine in 13.04.
When I click OK I get the window
"What would you like to do?"[INDENT]"Run in low graphics mode for just one session" brings up a "Stand by one minute while the display restarts" and then it never restarts.
I click OK and just get a blank screen.
[/INDENT]
[INDENT]"Reconfigure grahpics" I select OK and get a "How would you like to reconfigure your display?"
Both options "Use default (generic) configuration" and "Use your backed-up configuration" upon pressing OK do nothing but bring that same window back up.
I press "cancel" to go back to the "What would you like to do?" window

"Troubleshoot the error" brings up another window entitled "What information would you like to review?"
"Review the xserver log file" brings up the log file (which I really don't know what to do with)
"Review the startup errors" brings up an empty window
"Edit the configuration file" just brings the "What information would you like to review?" window again

"Exit to console login" just brings up the black screen.[/INDENT]


Is there a way I can get the screen working again?

---

### Post by NM5TF on 2013-12-23
you can try this....

reboot & press F6 key while still in boot mode...

select more options....

select "nomodeset"  option....

reboot.....

Tommy

---

### Post by Yellow Pasque on 2013-12-23
What kind of GPU do you have?

---

### Post by zmoney2 on 2013-12-23
NM5TF - I rebooted and pressed and held F6 during boot up and still got the same "running in low graphics mode" window and there wasn't a "nomodeset" option.

Temujin - I have a Dell 620 and the GPU is part of the motherboard.  It is a Nvidia 110m

---

### Post by deadflowr on 2013-12-23
Do you remember how you installed the original driver?

---

### Post by zmoney2 on 2013-12-23
I just put in the 13.04 and it found everything on it's own... I didn't have to do anything.

---

### Post by vasple on 2013-12-23
If you haven't remove the proprietary nvidia driver before the upgrade, that is propably the root of your problem. Remove it (backup and delete any xorg-files you have created), reboot and then reinstall it.

---

### Post by NM5TF on 2013-12-24
I had the same problem after install of Ubu 14.04.....

had to get rid of Nouveau...

used the following to fix it....

```
sudo apt-get install nvidia-current
```

try it to see if it fixes your problem...

Tommy

---

### Post by zmoney2 on 2013-12-24
Tommy, 
I tried the above and (ctrl-alt-F2'd over and logged in). It looked like it loaded a bunch of stuff and when it was done I rebooted. The same "running in low graphics" window came up.

I tried the above line again and got "nvidia-current is already the newest version".  (So I guess it did load a bunch of stuff the first time.)

---

### Post by deadflowr on 2013-12-24
Try booting back into the ctrl+alt+F2 again.
This time, after logging in run
```
ls /etc/X11
```
look to see if an xorg.conf file is listed.
if so, try
```
sudo rm /etc/X11/xorg.conf
```
this will remove that file.
Then try rebooting.
If it works then good, if not
Then try regenerating a new xorg.conf file
Again in the F2 tty2 console
```
sudo nvidia-xconfig
```
This will generate a new xorg.conf file.
See if that works or helps or really, anything.

---

### Post by zmoney2 on 2014-04-18
Sorry for the delayed response... due to work I'm pretty much off the grid for Jan-Mar... I'm getting back into this and really miss my Ubuntu.
I tried the above before I left and it didn't help.  Since everything on my laptop was backed up to the Ubuntu cloud I'm simply re-installing 13.04 and so far it seems to be going well.  I'm also downloading 14.04 and will try it live before committing to make sure I don't have the same graphics problem.
I don't know if simply keeping 13.04 on this laptop is a bad thing (especially since it works) but am wondering if not updating will leave my laptop vulnerable?

---

