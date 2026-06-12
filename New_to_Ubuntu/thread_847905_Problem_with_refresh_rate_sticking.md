---
title: "Problem with refresh rate sticking"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gizmobay on 2008-07-03
Hello All,

I just change my distro to Kubuntu and I'm having a slight problem with the refresh rate. The computer is a bit older so I'm using a GeForce 2 and the monitor is a Dell 1440FP. When I reboot or logout out, the refresh rate goes to 60Hz and this causes my screen to be shifted to the right so every time I login I have to change the refresh rate. I do this with krandrtray. I've edited the xorg.conf file to add the resolution with refresh rate but it doesn't seem to read the changes. I tried xorg server config but that just setup the keyboard and nothing else. How can I make the changes stick?

---

### Post by hakko on 2008-07-03
Try... (guessing):

Find this in /etc/X11/xorg.conf :
```


Section "Screen"
   Identifier    "Default Screen"
  Monitor    "Configured Monitor"
  Device    "Configured Video Device"
EndSection

```

Change to:
```

Section "Screen"
   Identifier    "Default Screen"
   Device    "Configured Video Device"
   Monitor    "Configured Monitor"
   DefaultDepth    24
   SubSection "Display"
     Depth    24
     **Modes      "1024x768_75"**
   EndSubSection
EndSection

```

The modes bit above shows 1024x768 res at 75Hz - change this your res and refresh.

Save xorg.conf and restart.

---

### Post by gizmobay on 2008-07-03
Thanks for the help. I made the changes and logged out then back in but for some reason the xorg.conf file wasn't read. As a test, I changed both the refresh rate and the resolution to 640x480 since the low res would be a dramatic change. None of these settings were changed. I thought maybe it was because krandrtray was setting the res so I killed this and re logged in but it didn't help.

---

### Post by gizmobay on 2008-07-03
I figured it out. I used $gtf 1024 768 70 . This gave me the Modlines. I then added these to my xorg.conf then rebooted and everything worked.

Under the Monitor Section, I added
UseModes "Modes[0]"

Then added a section of

Section "Modes"
   Identifier "Modes[0]"
   "cut and pasted the lines from the resulting gtf 1024 768 70"
EndSection

---

### Post by gizmobay on 2008-07-05
Found a better solution to the problem.

I installed envyng-core and then just ran envyng -t and this installed all nvidia drivers needed. Needed to do this to make Google Earth to work properly.

---

