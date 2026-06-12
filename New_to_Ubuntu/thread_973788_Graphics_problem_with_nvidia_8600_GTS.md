---
title: "Graphics problem with nvidia 8600 GTS"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Zantaskan on 2008-11-07
hello everybody-

I was using Gusty Gibbon for a while but never updated it to hardy hereon, so when version 8.10 came out i thought Id upgrade through version 8.04 to 8.10, just like the site recommended. Installed fine and all but when i restarted I got the error message saying that Ubuntu couldnt find my graphics card and had to use the lowest settings. I am using a nvidia 8600 GTS

I remember when i first installed Gusty Gibbon I had problems with my Graphics card , but it wasn't like this; only the graphics were laggy, I still got full resolution and everything. Now my picture is very grainy and everything is too large.

I tried the steps I remember doing to fix my graphics card under Gusty: 
       Using Envy program (I used the envy ng program this time but did int work. It seemed to, but when i restarted the monitor showed no signal available.)
       using restricted drivers
       trying to reconfigure xorg config

I will try to tweak with my problem some more, but maybe you guys can help. Thanks!

---

### Post by pgorillaman on 2008-11-07
What version driver are you using? You will want either 173 or 177. I have had better success with the 177 but my card is newer than yours.

---

### Post by Zantaskan on 2008-11-07
When I used Envy NG to install the driver, I believe the default one was 177, but it did not solve my problem. I think I should also go to nvidia's website and get the driver there, then see if it helps.

---

### Post by pgorillaman on 2008-11-07
Check and make sure. If not run ```
sudo apt-get install nvidia-glx-177 nvidia-settings
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig
```
Then restart, check that the driver is enabled under System->Administration->Hardware Drivers.
Backup up your xconfig (if there is one).
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
Then run ```
gksudo nvidia-settings
```
Make sure you save your new xorg.conf and restart.

---

### Post by Zantaskan on 2008-11-08
Ok I think Im on the right track, I can get teh correct display settings and the output looks alright. I am not really sure what I did, alst thing I did was uninstall a previous nvidia driver thrugh EnvY Ng... oh well

But when i check for hardware drivers it says I dont have any, and when i check in the Nvidia X server settings, it says I am not using nvida drivers,so i dont know if my problem is fixed. Also my computer's PSU is still running on high, like when it first boots up and i choose which OS to use etc., kinda hard to describe. 

Ill post if I get any more problems or if I can fix it

---

### Post by Zantaskan on 2008-11-12
OK I got it my graphic drivers fixed, I did another driver install through Envy NG. Now the system recognizes my graphics card and everything woot. 

Just curious, since I am running 8.04 Now, If I want to upgrade to 8.10, will I have the same problem with Ubuntu not recognizing my Graphic card/drivers?

---

