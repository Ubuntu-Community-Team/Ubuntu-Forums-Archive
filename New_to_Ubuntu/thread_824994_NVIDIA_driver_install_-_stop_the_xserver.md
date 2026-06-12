---
title: "NVIDIA driver install - stop the xserver"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by fxtr on 2008-06-10
Ubuntu 8.04  -  I downloaded the latest NVIDIA drive and on starting the install Iit wants the xserver stopped. I have not found the specific command to do this, The man xserver has lots of features and I am not sure on how stop it.

---

### Post by cocopuffz on 2008-06-10
press:
control + alt + f1 (this drops you into command line land...)

log in then...

"sudo /etc/init.d/gdm stop" to stop x

do your install. *make sure you know the dir (cd your to your dir path) it's in... and make sure you "chmod  +x _________________" the file so that you have permissions set

then you can "sudo /etc/init.d/gdm start" to restart x or I like to 

"sudo shutdown -r now" for a fresh reboot

You might need to "gksudo displayconfig-gtk"  if you're having issues with resolution after. It brings up a gui to edit your xorg file. Do a autodetect for your monitor. The plug and play driver seems ok. works for me seeing as how my monitor model isn't in the list. Sometimes the xorg.conf file doesn't contain the proper modes when you let nvidia do the config. "Sometimes." Good luck

Oh yeah. One more thing. =) Either book mark this, or write this down and store it somewhere cuz everytime there's a new kernel release, you're gonna have to recompile (part of the nvidia driver install process). We probably won't have to do this all the time once the new drivers are in the repos. Hopefully soon.

---

### Post by fxtr on 2008-06-10
Thank you!  Have printed it and about to start.

---

### Post by Barrucadu on 2008-06-10
Ctrl+Alt+Backspace
Stops X, and is much simpler than that other way.

---

### Post by fxtr on 2008-06-10
Stuck in low res. 
Video card and screen not recognized.
Under Applications when running the System Tools  NVIDIA X Server settings I get the message .. do not appear to be using the NVIDIA X Server just run as roo nvidia-xconfig....
gksudo displayconfig-gtk will not allow any changes in the video card, monitor or resolution.

---

### Post by fxtr on 2008-06-11
Reinstalled OS to fix problem. Will leave the NVIDIA drivers alone in the future.

---

### Post by rocketsami on 2010-12-14
I had that problem before.

reinstall the driver that is compatible with the OS. Go System>Administration>Hardware Drivers and then install the recommended one.

I think that is good

---

### Post by overdrank on 2010-12-14
Thanks. Back to sleep thread. :) Thread closed

---

