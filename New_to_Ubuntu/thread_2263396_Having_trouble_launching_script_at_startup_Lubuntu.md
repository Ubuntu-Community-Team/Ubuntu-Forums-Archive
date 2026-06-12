---
title: "Having trouble launching script at startup Lubuntu 14.04"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by Anders_Karlsson on 2015-01-31
Hello

I'm struggling to launch a script at startup.
i use the Xinput-calibrator for my touchscreen-KNX-pc, and need to put the commands in on every startup.
I have made a script, but can't get it to launch at startup.
When i execute the script manually, it works fine.

Here is my script:



#!/bin/bash
xinput set-int-prop "eGalax Inc. eGalaxTouch EXC7200-7545v1.000          " "Evdev Axis Calibration" 32 32540 747 32714 562
xinput set-int-prop "eGalax Inc. eGalaxTouch EXC7200-7545v1.000          " "Evdev Axes Swap" 8 0



can anybody help me with this?

Best regards,
Anders

---

### Post by ajgreeny on 2015-01-31
Make that script, call it **calibrate** and ensure that it runs, and is given execute permissions. Then put it in the bin folder in your home, if it exists, if not, make that folder, log out and in again to add it to the system $PATH.
See [http://askubuntu.com/questions/9848/what-are-path-and-bin-how-can-i-have-personal-scripts](http://askubuntu.com/questions/9848/what-are-path-and-bin-how-can-i-have-personal-scripts) for details of $PATH variable.

Now simply add the command **calibrate** to your startup applications list.  It should work fine; if not come back again.

Just a thought; does that script depend on the DE running before it is executed?  If so you may need to add a sleep time for it to work as expected.

---

### Post by Anders_Karlsson on 2015-02-01
> **ajgreeny said:**
> Make that script, call it **calibrate** and ensure that it runs, and is given execute permissions. Then put it in the bin folder in your home, if it exists, if not, make that folder, log out and in again to add it to the system $PATH.
See [http://askubuntu.com/questions/9848/what-are-path-and-bin-how-can-i-have-personal-scripts](http://askubuntu.com/questions/9848/what-are-path-and-bin-how-can-i-have-personal-scripts) for details of $PATH variable.

Now simply add the command **calibrate** to your startup applications list.  It should work fine; if not come back again.

Just a thought; does that script depend on the DE running before it is executed?  If so you may need to add a sleep time for it to work as expected.

Seems like i need a delay, yes. how do i add that? sleep=60 or something?
and do i add it in the script?

---

### Post by nerdtron on 2015-02-01
How do you call the script to launch at startup? in the startup applications? or on the rc.local?

If you need to wait for the desktop environment to load before you run the program, it's similar on how we use conky. 
See here: [http://ubuntuforums.org/showthread.php?t=1707947](http://ubuntuforums.org/showthread.php?t=1707947)

---

### Post by Anders_Karlsson on 2015-02-01
I got it working when I log out and in again, but not when i reboot. I use autologin.
Whats next? call it in the startup apps.

---

### Post by Anders_Karlsson on 2015-02-01
Now i got it working! added a 30-sec delay, and kabaaaang, is working:)

---

### Post by Anders_Karlsson on 2015-02-01
It seems that it doesn't work after all.
I've tried almost everything i found now, but after reboot, i need to log out and in again, then i have the script loaded.
Any suggestions?

My .desktop-file looks like this:
[Desktop Entry]
Encoding=UTF-8
Name=TouchscreenCalibration
Comment=RunCalibration
Exec=/home/stig/bin/touchpad.sh
Terminal=false
Type=Application


My touchpad.sh looks like this:
#!/bin/bash
Sleep=30
"My command"
"My command"


If i launch the script, it works fine.

---

### Post by CantankRus on 2015-02-01
**[COLOR="#B22222"]_Edit_[/COLOR]**
Just noticed your using **Sleep=30** in your script.
This will not run the sleep command. It will set a $Sleep variable and your subsequent commands will be run immediately.
Use **sleep 30**
(PS commands are case sensitive and spaces are important)


------------------------------------------------- 

Lubuntu should load quickly so if still doesn't work when rebooting you may have to disable  autologin.

---

### Post by nerdtron on 2015-02-02
## Sleep for 30 secs, then run the next commands
sleep 30 && echo "Hello world" && command here

---

