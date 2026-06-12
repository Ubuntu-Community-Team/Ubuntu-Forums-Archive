---
title: "Got Dual Monitor to work but now resolution changed to combine both!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-16
Ok have a laptop set at 1280x800 and a monitor at 1440x900.

So I installed the restricted drivers when they showed up on a fresh 8.04

After that I downloaded and installed the ATI Linux Catalyst Control Panel. Rebooted and loaded up the CCC to clone my monitor. Managed to set my external monitor to a different resolution.

Then I installed Compiz with the 4 windows and the cube.

Rebooted and my dual monitor resolution merged together to maybe 2000x1000 resolution on my laptop screen! I couldn't see the login section so just typed in my user name and password and yeah it logged in...

So I figured indeed resolution problem. Decided to see if I could spin the cube and yep I could... thou my screen was only focused on the far right part of this 2000x1000 cube.

Managed to remove this problem by just doing aticonfig --resolution=0,1280x900 on the recovery mode, but now I've lost the 1440x900 option for my monitor.

Is there any way to get it back and stop it from ever going to 2000x1000?

Also is there a recovery option like in windows system restore... if it wasn't a resolution problem then I would hav had no idea what change I did.

---

### Post by talsemgeest on 2008-05-16
I had a problem a bit like this, but my monitor scrolled when my mouse hit the side of the screen. I just decided to disable the secondary monitor because I didn't need it.

However I think I stumbled upon a line for the xorg.conf that might fix your problem that had something to do with autoscrolling. Can't find it now, but hopefully I have put you on the right track :)

---

### Post by talsemgeest on 2008-05-16
Oh, and as for backing up and restoring, save the file /etc/X11/xorg.conf and then copy it back when you want to restore the settings. EG ```
cp -p /etc/X11/xorg.conf ~/Desktop
``` to back it up, and ```
sudo cp -p ~/Desktop/xorg.conf /etc/X11/
``` to restore.

Hope this helps :)

---

### Post by Darksci on 2008-05-16
Ah my laptop monitor did that as well! It scrolled across the screen at one point.

I guess I should just remove ATI CCC and just use the restricted drivers. Seemed to hav just caused me problems.

Why is it so hard to assign one panel to laptop lcd and one to external monitor lol (without cube compiz).

Oh as for the restore thing I mean a full backup of all system files? I mean Xorg.conf is just display. But cheers anyway!

---

### Post by talsemgeest on 2008-05-16
Oh, if you want to back up everything you can use quickstart. Great little program which specializes in backing up. The forum for it is here: [http://quickstart.phpbb.net/index.php](http://quickstart.phpbb.net/index.php)

---

### Post by Darksci on 2008-05-16
Any other program which can do backups? ^^;

---

### Post by lecter255 on 2008-05-16
hey guys I want to get my external monitor to work also.

Right now, my laptop monitor display up to 1280X800 and I can only get my external monitor to display up to that resolution, but my external monitor's max resolution is 1920X1200. I got that to "work" by configuring it through System->preferences->screen resolution. How can I just use the external monitor and not the laptop monitor when the external is plugged in and utilize the full resolution on my external monitor? My external monitor is a 24" samsung monitor. I have been trying to mess with xorg.conf but no success. 

Please please help this problem has pushed me back to vista for a while :( *shiver*

---

