---
title: "[SOLVED] Changes in GUI behavior after update"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Garrigus Carraig on 2013-03-03
[Ubuntu 12.04 32-bit, Unity 5.18.0]
On Friday morning I installed the recommended software updates, as I always do (list included at the end of this message). The next day, after rebooting, the GUI evinced some changes in behavior as follows:
[LIST]
[*]Launcher icons reverted to larger size (48x48?). And I can't shrink them back, because the icon size slider bar in the System Settings Appearance pane is gone. 
[*]Hitting ctrl-alt-{arrow key} to switch workspaces no longer animates the process; the transition is instantaneous. 
[*]Holding down the Super key no longer brings up the pane of all the keyboard shortcuts; it brings up the shortcut numbers over the launcher icons, and stops there. 
[*]Hitting Super-W no longer does that Mac OS X Exposé-style "show all windows" trick. 
[*]The alt-tab behavior for switching windows is much less flashy now. The row of icons is much smaller. It shows one icon per window, instead of one per application. Pausing over an app icon used to make it expand into all the windows the app had open; that behavior is gone. While alt is held down, it does show a white outline of whatever window is selected. 
[/LIST]
 None of this is important. But it seems that some or all of these differences resulted directly from the software updates, so I'm curious & in general would like to improve my understanding of what these packages do.

Thanks in advance. Friday's updates are listed below, as promised.

```
cat /var/log/dpkg.log | grep -i status\ installed
2013-03-01 11:26:56 status installed libssl1.0.0 1.0.1-4ubuntu5.7
2013-03-01 11:26:57 status installed libc-bin 2.15-0ubuntu10.3
2013-03-01 11:27:42 status installed man-db 2.6.1-2ubuntu1
2013-03-01 11:27:42 status installed ureadahead 0.100.0-12
2013-03-01 11:27:43 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-03-01 11:27:43 status installed desktop-file-utils 0.20-0ubuntu3
2013-03-01 11:27:43 status installed gnome-menus 3.4.0-0ubuntu1
2013-03-01 11:27:45 status installed libdbus-glib-1-2 0.98-1ubuntu1.1
2013-03-01 11:27:45 status installed libgl1-mesa-dri 8.0.4-0ubuntu0.4
2013-03-01 11:27:46 status installed libglapi-mesa 8.0.4-0ubuntu0.4
2013-03-01 11:27:46 status installed libgl1-mesa-glx 8.0.4-0ubuntu0.4
2013-03-01 11:27:47 status installed libxatracker1 8.0.4-0ubuntu0.4
2013-03-01 11:27:47 status installed libglu1-mesa 8.0.4-0ubuntu0.4
2013-03-01 11:27:48 status installed sudo 1.8.3p1-1ubuntu3.4
2013-03-01 11:27:48 status installed openssl 1.0.1-4ubuntu5.7
2013-03-01 11:27:49 status installed firefox 19.0+build1-0ubuntu0.12.04.2
2013-03-01 11:27:50 status installed firefox-globalmenu 19.0+build1-0ubuntu0.12.04.2
2013-03-01 11:27:50 status installed firefox-gnome-support 19.0+build1-0ubuntu0.12.04.2
2013-03-01 11:27:50 status installed firefox-locale-en 19.0+build1-0ubuntu0.12.04.2
2013-03-01 11:27:51 status installed xserver-xorg-video-nouveau 1:0.0.16+git20111201+b5534a1-1build3
2013-03-01 11:27:51 status installed libc-bin 2.15-0ubuntu10.3
```

---

### Post by sully101 on 2013-03-03
Hi Garrigus,

I have those updates also and am not experiencing any of those behaviors. As a suggestion you may have logged into a 2D session instead of 3D? Try logging out click the ubuntu icon next to your user name and select the 3D option, then login

---

### Post by Garrigus Carraig on 2013-03-04
I double-checked and I always log into 3D by default. But (see below) it looks like my system doesn't (consistently) handle 3D. I'm guessing that's the issue.
```

:~$ !681
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7000M / nForce 610M/integrated/SSE2/3DNOW!
OpenGL version string:  1.4 (2.1.2 NVIDIA 302.07)

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```

---

### Post by sully101 on 2013-03-04
Sorry I'm ati graphics here. Yes that looks like the issue :( ```
glxinfo | grep direct
``` should return "direct rendering: Yes" if you have "proprietary drivers" installed ?  I know some laptops have their own implementation of the nvidia chipsets and I did read somewhere about problems with the intel HD2000, HD 3000 etc.
There are plenty of how to's about getting the nvidia binarys installed. If you installed them already from the nvidia site ( and you get a direct rendering: No ) then they are not working and you would need to follow a how to on updating them. If not then "System Settings" > "Additional Drivers" or from the command line ```
jockey-gtk
``` or  ```
jockey-text
```

You probably want to start here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by Garrigus Carraig on 2013-03-05
I was getting a "Direct rendering: no". Also, [FONT=courier new]jockey-text -l[/FONT] was telling me none of my drivers was enabled.

With your help, Sully, I think I figured it out. My system does  not officially support Unity 3D. Somehow I was able to install the  Nvidia 302.07 drivers and 3D was working. Then the update broke that. I  could probably keep 3D going by reinstalling the 302.07 drivers every  time something went awry, but I'm not that invested in 3D, so I fired up  Additional Drivers and installed the 295.40 drivers and am fine with  2D. Thank you!!

---

### Post by sully101 on 2013-03-05
I'm guessing that the 302.07 drivers were downloaded from the nvidia site ? If they were then things will probably break on every kernel upgrade. They need to be uninstalled if they were. I have had a lot of experience with black screens/binary drivers, and there not fun when your new at linux. There is a how to here [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") read it well! Then reinstall the ones you see with "System Settings" > "Additional Drivers" those ones will handle the kernel upgrades correctly. I'm posting this here just in case someone else stumbles apon this thread. I found this also with someone else in your predicament [http://askubuntu.com/questions/136143/12-04-nvidia-problem-which-card-series-work]("http://askubuntu.com/questions/136143/12-04-nvidia-problem-which-card-series-work") 
QUOTE
> My advice in your case: Remove all old drivers and install the nvida-173 driver, it should be sufficient to run Compiz (I did that back in 2008 with 08.04, version back than was 140 or 160), however the chip may not be fast enough to run Unity, you could try to disable blur in CCSM, if that doesn't help you have to use Unity 2D.

Having said all that > If it aint broke dont fix it!

---

