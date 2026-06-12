---
title: "Flash not working at all 12.04"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by BrianV on 2012-10-31
I'm running 12.04 32-bit on a P III 1133MHz with an NVIDIA 6200 256 MB graphics card. System Settings/Details shows Graphics Unknown.

Neither Firefox nor Chromium will display videos. For example, when trying to access TED videos, Firefox displays a blank screen where the video should appear and Chromium show a blank screen with a "Couldn't load plug-in" message. 

Don't know if the Graphics Unknown and lack of video are related.

I have tried all the solutions offerred in other posts related to flash plug-in problems, with no good results.

Suggestions to get to a clean starting point, then some diagnostic help would be greatly appreciated. Maybe I need a newer computer or an older version of ubuntu?

---

### Post by Pilot6 on 2012-10-31
New flash will not work on Pentium III. You need to download flash 10.3 from [here]("http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.29_archive.zip"), extract file libflashplayer.so and copy it to /usr/lib/flashplugin-installer/

After that flash will work. You need also to use synaptic and disable updates of flashplugin-installer package.

---

### Post by BrianV on 2012-10-31
Pilot 6:

I have the file extracted. How do I copy it to the correct destination? How do I follow the rest of your advise, to turn off updates?

Thanks, Brian

---

### Post by Pilot6 on 2012-10-31
Put the file to your home folder. Then open terminal and run the command:
```
sudo cp ~/libflashplayer.so /usr/lib/flashplugin-installer
```
You will be asked to enter password. Do it. Nothing will be displayed when you enter the password.
After that if you restart your browser, flash will start working.

You may delete the file from your home folder, if everything is OK.

---

### Post by Pilot6 on 2012-10-31
Then you need to disable updates, because sometime later an update will overwrite your flash and it will stop working again.
Install Synaptic using Software manager or run command
```
sudo apt-get install synaptic
```
Start synaptic, enter flasplugin in Search field and select flashplugin-installer. Then go to menu (top of screen) and select Package -> Block version.

Enjoy!

---

### Post by Pilot6 on 2012-10-31
Flash will work in all browsers but Chrome. if you want to use Chrome, you need to disable pepperflash. But I think that in new versions it is disabled automatically on old cpu's. So it may work even there.

---

### Post by BrianV on 2012-10-31
Pilot 6:

I have done the copy part. /usr/lib/flashplugin-installers now contains install-plugin* and libflashplayer.so

Not sure what I should do next?

---

### Post by Pilot6 on 2012-10-31
Does flash work? If it does just do, what I said in Synaptic.

---

### Post by BrianV on 2012-10-31
Pilot 6:

Thank you. It seems to work, though I haven't tried Chromium yet. Your assistance was bang-on, and fast! Thanks again.

Brian

---

### Post by Pilot6 on 2012-10-31
It does not matter which browser. They all use same flash except Chrome. Do not forget to use Synaptic, or flash will die again.
The best way to test flash is to go [here]("http://helpx.adobe.com/flash-player.html")

---

### Post by NikTh on 2012-10-31
Good Job Pilot6 :) 

BrianV you can mark the thread as solved (by clicking thread tools)  :) 

Thanks

---

