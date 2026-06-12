---
title: "Video Driver Question"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Loki*PI on 2008-05-30
Running Hardy 8.04
Have a nVidia Corporation GeForce 8500 GT video card

When I use the generic Ubuntu drivers I have a good screen with 12xx by 1024 resolution at 75 Hz.

I used Sys -> Admin -> Hard Ware Drivers - to install the NVIDIA driver. After a reboot I get a good screen but resolution drops to 1024 x 760 at 50 Hz.

I much prefer the higher resolution. Any suggestions other than using the default drivers which do not support acceleration or 3D.

Thanks

---

### Post by EXCiD3 on 2008-05-30
Check out starcannons post here, works like a charm: [http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

---

### Post by quelx on 2008-05-30
try installing **nvidia-settings** from **synaptic** and see if that lets you change the resolution.

---

### Post by Tatty on 2008-05-31
I have a 8500GT.  I installed the drivers with envy and it worked fine.

```
sudo apt-get install envyng-gtk
```

(replace gtk with qt if you are using kde.)

Then you will find envy sitting in applications->system tools i believe.

---

### Post by Loki*PI on 2008-05-31
Hi EXCiD3 - thanks - I've gone through your procedure 3 times, but not too good of results.  I have only the most basic video now.  I can follow your procedure, that is understand it, and I can get back to where I was ok.  I'm wondering why it didn't work.  Any thoughts?

---

### Post by Loki*PI on 2008-05-31
EXCiD3 - I think the xorg is not being updated/recreated when the driver is installed.  The driver installation goes through with no issues, but when I return to the GUI it is in basic mode.  The xorg.backup has been over written - my mistake - so that is no longer viable.  There is a utility at Nvidia that is suppose to make an xorg but I couldn't get that to work.  I've tried reinstalling the orginal drivers using "Hardware Driver" but that doesn't seem to update the xorg.  Xorg is calling a 640 x 400 configuration.
I'm open to suggestion.  

Thanks

---

### Post by Loki*PI on 2008-05-31
EXCiD3 - I got it.  The Nvidia drivers are loaded and working.  Resolution now at 12xx.  Odd thing Nvidia drivers do not show up in "Hardware Drivers" but they are running.  

Thanks EXCid3 and the others.

---

### Post by EXCiD3 on 2008-05-31
Hey sorry i couldnt get back to you sooner! This dialup and I dont get along very well! ;)

Glad you got it working. I wouldn't worry about it not showing up in Hardware Drivers, thats just something to **try** to help users, but it sure doesn't do near as good of a job as installing the drivers by hand. FYI, nvidia-xconfig is the command to have the nvidia driver autoconfig the xorg for you. Its what runs when you are compiling the driver and it asks if you would like to have it automatically configure for you. Sorry it took several times to work, but ive had the same results various times especially back in Feisty. The first couple of times just didnt work and i dont know why!

---

### Post by pancakelizard on 2008-06-01
EXCiD3 - I did the steps you provided and everything seemed to have worked however now my resolution is worse and whenever I go to the NVIDIA X Server Settings application, it states that "You do not appear to be using the NVIDIA X Driver. Please edit your X Configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

---

### Post by nantax on 2008-06-01
Thank you for you post EXCiD3. I found it to be very helpful compared to the instruction at the nvidia forum. :KS:KS:KS

---

### Post by EXCiD3 on 2008-06-01
> **pancakelizard said:**
> EXCiD3 - I did the steps you provided and everything seemed to have worked however now my resolution is worse and whenever I go to the NVIDIA X Server Settings application, it states that "You do not appear to be using the NVIDIA X Driver. Please edit your X Configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

For some reason it doesnt work every time. Just run through the steps a couple of times and it should work. I had the same problem as you did, just something doesnt get done correctly. In fact once compiling the driver failed, but i tried it again and everything worked fine.

---

### Post by hmgp on 2008-06-04
Just great. I've been killing my head on this one for some hours now and you did it. Thank you!

---

