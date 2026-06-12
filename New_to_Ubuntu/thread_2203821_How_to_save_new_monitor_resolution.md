---
title: "How to save new monitor resolution"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by kaspin2 on 2014-02-05
Since changing my monitor to a 22” TV, the standard 4:3 resolutions of 1024x768 and 800x600 in Ubuntu 12.04 are too wide or too big. Using randr I found that 1224x768 (3:2) was fine and this became an option, with the 2 standard resolutions, in the drop down box in the “displays settings” window.
[ATTACH=CONFIG]250116[/ATTACH]
The problem is how to preserve it before rebooting. I've tried changing the values in xml.config (no effect – file since deleted) and putting into /usr/share/X11/xorg.conf.d/  (or /home/../usr/share/X11/xorg.conf.d) a file labelled “10-monitor.conf”, the contents of which are:

 

 Section "Monitor"
   Identifier "Monitor0"
   "1224x768_60.00"   76.00  1224 1288 1408 1592  768 771 781 798 -hsync +vsync
 EndSection
 Section "Screen"
   Identifier "Screen0"
   Device "VGA1"
   Monitor "Monitor0"
   DefaultDepth 24
   SubSection "Display"
     Depth 24
     Modes "1224x768_60.00"
   EndSubSection
 EndSection
 

 The Monitor0 values came from entering “cvt 1224 768 60” in a terminal, although I'm not sure if the entry above under Modes is correct (I also tried “VGA1 1224x768_60.00").
 

 However, after inserting the above file and rebooting I got a black screen and nothing, so had to reboot in the recovery mode, where I get a terminal which enables me to delete the above file, after which I can reboot normally, but to the default values.

 

 I've also tried changing Grub values as explained in:
 [http://askubuntu.com/questions/127851/change-boot-screen-resolution](http://askubuntu.com/questions/127851/change-boot-screen-resolution)
 but to no avail.
 

 Can anyone please tell me what I'm doing wrong, or propose a different way of  keeping permanently the new monitor values? Many hugs in advance...

 

 Kaspin

---

### Post by ajgreeny on 2014-02-05
Try adding that same text to /etc/X11/xorg.conf which may not exist, but if not make a new file of that name with ```
gksudo gedit /etc/X11/xorg.conf
``` and then logout and login again.

---

### Post by kaspin2 on 2014-02-06
Many thanks, ajgreeny, for replying so quickly. Unfortunately I again got the black screen and had to delete xorg.conf from /etc/X11/ and reboot in order to get back a display.I've been getting occasional warnings about low graphics mode and the message "Could not apply the stored configuration for monitors" on start up. Apparently it is trying to use my mode, as one of the lines is "
CRTC 63: trying mode 800x600@60Hz with output at 1224x768@60Hz (pass 1)  "
Maybe there's an issue with my Intel 82865G graphics controller. I'll keep trying to find a solution, and in the meantime I can use Autokey to input the xrandr newmode and addmode parameters, so it's fairly quick to set up the new resolution at the start of each session.
I'd be grateful for any other ideas from anyone, and will post a solution if I find one.... Kaspin

---

### Post by kaspin2 on 2014-02-09
Just to say I've gone down a different road and written a script which incorporates the xrandr parameters, and added it to the start-up applications. So problem solved, as far as I'm concerned. Kaspin

---

### Post by Iowan on 2014-02-09
> **kaspin2 said:**
>  So problem solved, as far as I'm concerned. Kaspin[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) :)

---

