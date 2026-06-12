---
title: "Err... I did something bad..."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by lomandel on 2008-10-15
well, I was trying to get my visual effects to work because i was getting an error that said "The Composite Extension is not available" So i did a little looking arround and came accross this post. [http://ubuntuforums.org/showthread.php?t=637101](http://ubuntuforums.org/showthread.php?t=637101)

I followed some of the instructions in there and after i typed compiz, everything became unresponsive.. so i restarted. when ubuntu started up, my mouse became a black x and a window popped up saying that i had to run in compact graphics mode or something.. there was an option to configure my video drivers, so i did. When i choose the drivers, i was able to log in to my user.. but the resolution was stuck at 800x600. I went in to my restricted drivers manager and checked the ati driver and restarted my computer... After the ubuntu loading bar, i heard the sound that plays when you enter your username and password, but the screen was black.. i typed my info blindly and got loged in, but only a small portion of my desktop was visible on the top left of my moniter.. It Looked exactly like this..

[http://picboost.com/images/2008/March/13/Screenshot.png](http://picboost.com/images/2008/March/13/Screenshot.png)
(from the post [http://ubuntuforums.org/showthread.php?t=723006](http://ubuntuforums.org/showthread.php?t=723006) )

I am totally stuck.. and back in windows trying to figure out what to do.. any help would awesome. 

Sorry for the long post, 
Steve

---

### Post by eternalnewbee on 2008-10-15
> **lomandel said:**
> well, I was trying to get my visual effects to work because i was getting an error that said "The Composite Extension is not available" So i did a little looking arround and came accross this post. [http://ubuntuforums.org/showthread.php?t=637101](http://ubuntuforums.org/showthread.php?t=637101)

I followed some of the instructions in there and after i typed compiz, everything became unresponsive.. so i restarted. when ubuntu started up, my mouse became a black x and a window popped up saying that i had to run in compact graphics mode or something.. there was an option to configure my video drivers, so i did. When i choose the drivers, i was able to log in to my user.. but the resolution was stuck at 800x600. I went in to my restricted drivers manager and checked the ati driver and restarted my computer... After the ubuntu loading bar, i heard the sound that plays when you enter your username and password, but the screen was black.. i typed my info blindly and got loged in, but only a small portion of my desktop was visible on the top left of my moniter.. It Looked exactly like this..

[http://picboost.com/images/2008/March/13/Screenshot.png](http://picboost.com/images/2008/March/13/Screenshot.png)
(from the post [http://ubuntuforums.org/showthread.php?t=723006](http://ubuntuforums.org/showthread.php?t=723006) )

I am totally stuck.. and back in windows trying to figure out what to do.. any help would awesome. 

Sorry for the long post, 
Steve

Log into Ubuntu in Safe mode and try to reconfigure your screen resolution. Trouble is, ATI is not so Ubuntu frienly as Nvidia...
Good luck

---

### Post by Orange_and_Green on 2008-10-15
You might also want to log into your regular installation (blindly), then press ctrl+alt+F1. This will bring up a terminal. Log into it.

From there, you can try undoing the changes you made to /etc/X11/xorg.conf (or restoring a backup copy if you made one), or running ```
dpkg-reconfigure xserver-xorg
``` (although there is no telling what you'll end up with after this last try...)

Keep us posted. Keeping my fingers crossed for you...:KS

[EDIT] Note: Once you are done in this terminal and want to leave, you can press ctrl+alt+F7 to go back to the regular screen and restart from there, or simply restart from the terminal by typing
```
sudo reboot
```

---

### Post by hyper_ch on 2008-10-15
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by lomandel on 2008-10-15
Ok so, I managed to turn off the restricted driver that was causing only a small portion of my desktop to show. That bought me back to my desktop in 800x600. from there i tried to use 
```
dpkg-reconfigure xserver-xorg
```
After manually setting my driver, it asked me to name my card then determine what bus it operated from if i had more then one graphic card. for some reason it wouldn't let me press enter. I gave up on that and went to system>admin>screens and graphics, and tried to set my cards driver there, which still didn't work. so i gave up and went to sleep. I woke up about 10 mins ago and when my login screen came up it was the normal resolution.. (AHH YES) But when i logged in, it was back to 800x600. It gave me the option to readjust it to 1024x768 in system>preferences>screen resolution. it looks fine now, but when i checked the screens and graphics setting again, it said   the resolution was still running at 800x600....strange. i guess i hope it stays normal for now

---

