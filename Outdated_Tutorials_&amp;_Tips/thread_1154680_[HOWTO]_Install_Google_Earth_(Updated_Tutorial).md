---
title: "[HOWTO] Install Google Earth (Updated Tutorial)"
date: 2009-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by collinp on 2009-05-10
[COLOR=Red][B][SIZE=5][COLOR=Black]Installing Google Earth
[/COLOR][/SIZE][/B][SIZE=5][COLOR=Black][SIZE=2]The steps to install Google Earth are outlined below:

First, we need to get Google Earth
Open a terminal and type:
[/SIZE][/COLOR][/SIZE][/COLOR]```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
```After that completes, type:

```
chmod +x GoogleEarthLinux.bin
```That gives the Google Earth file permission to execute - required for any file that you need to execute.

Lastly, type:
```
./GoogleEarthLinux.bin
```This executes the Google Earth installer, which will install Google Earth. It will do a few checks on the archive integrity, then it will start the installer. The defaults should be fine for most people, just click "Begin Install". Once that completes, you have a working Google Earth install! To run it, open a terminal and type "./googleearth" (without the quotes) .

[SIZE=3][B]Uninstalling Google Earth
[/B][SIZE=2]To uninstall Google Earth, open your Home Folder (Places -> Home Folder). Inside there, you will find a directory called "google-earth". Double-click to enter that directory. Inside there you will find a file named "uninstall". Double-click that and, when prompted, click "Run". It will automatically uninstall Google Earth **WITHOUT PROMPTING YOU!** Make sure you really want to remove Google Earth, as it will not prompt you before removing it.

I hope this tutorial helps everyone to install Google Earth, and if you have any questions, post them in this thread! Cheers!
[/SIZE] [/SIZE]

---

### Post by jpeddicord on 2009-05-11
Approved; thank you for your tutorials & tips contribution. :)

---

### Post by Tybion on 2009-05-14
If you get a warning that GE is running in 'OpenGL' mode and might run slowly, check if you are using a proprietary video driver.  In Xubuntu, you do this by choosing System->Hardware Drivers from the main menu.

If a proprietary driver is available for your PC, I suggest that you 'activate' it and reboot.  Google Earth was unusable when I was using a generic video driver, but it is running beautifully now that I am using the Nvidia proprietary video driver - and that is with an older 1.x gHz Pentium4 with 1 meg of memory and just a video card that came with the motherboard.

Congratulations Google on supporting Linux!

---

### Post by freeediver on 2009-06-28
O well, just like all the other installs I have tried this also crashes my system when it attempts to run.
How can the original instructions modified to install an older hopefully more stable version of GE, 4.2 maybe?
Thanks

---

### Post by MichaelRX8 on 2009-06-28
Thanks! I had tried to install google earth out of ubuntu tweak with no success (it would start then vanish). This one works great, thanks again!

---

### Post by freeediver on 2009-06-29
Yea it's fixed, it was a simple fixed once I pressed the correct buttons.
It was a driver issue.
I had to open up hardware drivers then I found out 3D was not selected. I checked to enable 3d, installed the driver, rebooted per instructions, presto GE now works.

---

