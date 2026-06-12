---
title: "Pano mag configure ng monitor refresh rate?"
date: 2008-05-05
forum: Philippine Team
---

### Post by NakedSnake on 2008-05-05
guys, i need help sa refresh rate ng monitor.
crt monitor lang to but when i tried to install Ubuntu 7.10 and Hardy
the resolution is only 800x600 which made the icons and windows big
eh gumagana naman siya sa xubuntu 6.10

Installed Ubuntu 7.10 [Ok]
Configured xserver-xorg [OK]
Used GNOME Session  [OK]
Logged in @800x600
did dpkg-reconfigure xserver-xorg
did dpkg-reconfigure -phigh xserver-xorg
change resolution to 1024x768 [FAIL]
pero sa xubuntu gumagana 1024x768@60hz
did # cvt 1024 768 in the terminal
pasted modeline result on xorg.conf

---

### Post by Samhain13 on 2008-05-05
Hummm, I just installed Hardy and finished tweaking my display settings.
There's a utility under Applications > Other > Screens and Graphics. For my monitor, some 21" CRT that I got from a surplus shop:

1. Clicked on "Model"
2. Under the Manufacturer column, picked "Generic" (top choice)
3. Under the Model column, picked "Monitor 1600x1200"
4. Click "Add", then OK.

It'll take a moment to do its thing and when it's done, it will tell you to logout for the changes to take effect. When you log back in and check /etc/X11/xorg.conf, you'll see that it's modified, also System > Preferences > Screen Resolution will give you a lot more options.

One weird thing I noticed when I logged out though was that the login screen was way too big. Perhaps a restart is going to set things in order but I haven't restarted yet as I'm installing other things.

I hope this helps you, even a little. :)

---

### Post by NakedSnake on 2008-05-06
thanks in responding to my problem.

I still dont get my optimal resolution in my screen.
800x600@60Hz

funny thing is Xfce in Xubuntu 7.10 can display 1024x768@60Hz
and my monitor didnt have any problems.
now when I reformatted, and installed, Ubuntu 7.10 on my pc.
In can only display 800x600 no matter what I do with the
resolutions settings, in xorg.conf, is GNOME and Xfce different
when it comes to monitors? and sometimes my CRT displays 
Our of Range / Frequency.

Im a little frustrated with my PC. maybe if I play along with the settings 
a lil bit more, I will soon find the solution.

Thanks again.
will let you know when I solved this.

---

### Post by Samhain13 on 2008-05-06
I can't say how similar or different Gnome and Xfce are, sorry.
Goodluck on finding a solution though. :)

---

