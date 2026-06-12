---
title: "screen res. on nvidia x server"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Techarmy on 2008-11-11
ok i got nvida x server thing yesterday and my screen i can get it to display 640x480 of my 1024x786 screen so when i move my mouse it moves around the 1024x786 but i want it to display all of it not just the little  that it shows what do i do:confused: :confused: :confused: please help

---

### Post by mr.v. on 2008-11-11
Go to the nvidia settings manager.

open a terminal window and type
```
sudo nvidia-settings
``` to open the nvidia settings and play with the monitor tab and detect the display and also change the resolution from there. Then when you're done getting everything to look right you can click the Save to X config file button to keep the settings.

---

### Post by Techarmy on 2008-11-11
yea but all it says is auto, 640x480, and like 300x 100 something like that and i used to have 800x600 till i installed this and i cant get it any better

---

### Post by Techarmy on 2008-11-11
bump bump bump

---

### Post by mr.v. on 2008-11-12
go to System|Administration|Nvidia X Server Settings
-click X Server Display Configuration on the left side
-click Detect Displays at the bottom.
-under resolution select 800x600 and select 60Hz or whatever is closest to 60Hz.
-click the "Advanced..." button and see what it says under "Panning: " it should say 800x600. If it doesn't, type 800x600.
-click <Apply> button.

What happens? also post monitor brand, monitor specs, and nvidia card model.

---

### Post by m_l17 on 2008-11-12
Try this:

[http://ubuntuforums.org/showpost.php?p=6134272&postcount=4]("http://ubuntuforums.org/showpost.php?p=6134272&postcount=4")

---

