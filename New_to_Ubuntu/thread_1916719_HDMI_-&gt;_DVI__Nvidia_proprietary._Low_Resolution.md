---
title: "HDMI -&gt; DVI  Nvidia proprietary. Low Resolution issue."
date: 2012-01-28
forum: New to Ubuntu
---

### Post by ==Troy== on 2012-01-28
Nvidia 9400GT video card
proprietary driver.
Ubuntu 10.04 LTS.

HDMI out -> DVI in cable. (HDMI out from PC, DVI into the monitor).

Things that work :

Nvidia driver recognises both the laptop screen, and the monitor. (DFP - 0 and DFP - 1)
Driver correctly works with the laptop screen.
Driver can display on the monitor, but only at max of 640x480.

Things that dont work :

Unable to set any resolution above 640x480
Driver says DVI single-link connection
Changing x-server config manually does not work. (setting native 1440x900 resolution).


I have searched the forums, but none of the solutions seemed to work for me so far.

Am I missing something?

Thanks for any help :)



Edit :

Apologies! Resolved the issue.

The monitor was not correctly providing EDID.

Steps to fix :

Connect via VGA.
Go to nvidia settings. Go to screen menu. Press Aquire EDID
Save edid somewhere in your home folder
Transfer the edid to /etc/X11/
Add the custom edid option to xorg.conf
restart X
and now it works!

---

### Post by llamabr on 2012-01-28
Well done.  It's satisfying when you solve it yourself.

---

