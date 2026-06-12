---
title: "[HOWTO] Fixing ATI driver problems"
date: 2008-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Kronie on 2008-06-18
Hey ppl, I had this issue with ATI videocard driver when I had my desktop plain white(for some people it can be black) after I login to my account. then I figured out the solution, and decided to share it wih you incase you have same problem.. This tutorrial will help ypu fix most of the ATI driver problems.

THIS IS ONLY FOR ATI VIDEO CARDS!
this helped me fix my x600 videocard, also, this was reported to be working manual from user with x1600 videocard. This was tested on ubuntu 8.04, I give you no guarantee that in will work on older versions.
You have to do this at your own risk, I am not responsible for whatever happens with your OS/software/hardware. But if you follow the tutorial exactly the way it is, you'll be fine. 

Here we go:

**Step 1**: In synaptic package manager(System-> Administration-> Synaptic..) remove packages named 
            ```
xserver-video-ati
``` and ```
xorg-driver-fglrx
```(this is the one that you see in 	
	'Hardware Drivers'

**Step 2**: Restart your PC. After restart, your screen will be low-resolution, and you will get the message  	saying that the system is running in low-quality mode. Ignore all settings and press continue.

**Step 3**: Log in to your account(don't try to change resolution, what you will see will be maximum 	resolution you can choose). Go to System-> Administration ->Hardware Drivers, and put a 	check on “Use Driver” near “ATI Accelerated Graphics Driver”. This will install a fresh copy of 	previously deleted  xorg-driver-fglrx. After installation it will prompt you to restart. Ignore it for 	now.

**Step 4**: In synaptic, install ```
xserver-video-ati
```, and then restart.

**Step 5**: Log back in to your system, go to System-> Administration-> Hardware Drivers, and put a 	check on “Use Driver” near “ATI Accelerated Graphics Driver”, and then restart.
[B]
Step 6[/B]: Log in to your account. If you still having issues, continue reading this tutorial. Otherwise, skip 	to step 14.
------------------------------------------------------
**Step 7**: Restart the X server by pressing Ctrl+Alt+Backspace.

**Step 8**: In the login menu, click on the button in bottom left corner(options button), and choose 	“FAILSAFE Gnome” session. Then enter your login to your system. Doing this will make your 	system load only the necessary for operation drivers(somewhat a safe mode in windows)

**Step 9**: Go to terminal and type ```
sudo gedit /etc/X11/xorg.conf
``` this will open the X config editor.

**Step 10**: In the text file that opened, loog for “Driver “***”” in the “Device” section. Its the very first 	section from top.

**Step 11**: Change whatever stands after “Driver” to fglrx, so that it will look like ```
Driver 	“fglrx”
``` and save.

**Step 12**: After that, open a termnal, and type ```
sudo aticonfig –initial -f
```

**Step 13**: Restart the machine, and then login as you usually would.

**Step 14**: Enjoy, and dont forget to thank me :P

---

### Post by parabolee on 2008-07-09
THANK YOU!!!!!!!!!!!!!!!

I tried to install the catalyst control panel and it screwed my whole system up, I even tried everything in your instructions EXCEPT removing xserver-video-ati and then installing it again! That step was preventing me from fixing the system!

You might want to add that in 8.04 it's listed as "xserver-xorg-video-ati".

THANKS! I can finally sleep! :-D

---

### Post by Aenima99x on 2008-07-20
Thank you!!! 
Been fighting with these damn drivers for a couple days.
You rock!  :guitar:

---

### Post by kajillin on 2008-07-20
well it helped until i restarted again. thanks though.

---

### Post by JagDragon on 2008-07-21
This issue is caused by a kernel update through the automatic updates. The fglrx driver is propriatary software, and is therefore not carried forward properly when the linux kernel updates. Simply reinstall the drivers the way you did the first time, and all will be well ;)

---

### Post by sanus|art on 2008-07-21
Just install 'envyng-core envyng-gtk', install the drivers trough it and this will probably disappear forever.

---

