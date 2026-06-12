---
title: "no sound on zotac nano ad10"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by catman915 on 2014-01-08
I installed ubuntu 13.1 on my zotac on which I already have XBMC 12 working, I use hdmi output to receiver and everything works fine. There is no sound in Ubuntu 13. Would appreciate any assistance. Thanks

---

### Post by squakie on 2014-01-09
That uses an AMP APU which has a AMD/ATI Radeon graphics.  There is a boot option you need to add in order form the HDMI option to show under sound seettings.  That option is  radeon.audio=1  and you can manually add it at boot to be sure it works for you.  If it does, you edit the /etc/default/grub file:

- sudo gedit /etc/default/grub

- find the line near the top that says something like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

- add this line right after that one:

GRUB_CMDLINE_LINUX="radeon.audio=1"

- save the file and exit the editor

- type sudo update-grub

- just reboot now and see if the option shows in the sound settings.  If so just select it and sound will be output via the HDMI (assuming you have the proper cable - a normal HDMI cable should work).

---

### Post by catman915 on 2014-01-09
Thanks for the tip. It worked fine on Ubuntu 12.04lts. I also have Ubuntu 13.1 installed with the same problem and tried your fix on it but it didn't work. I don't see an hdmi choice in audio settings even after the change.

---

### Post by squakie on 2014-01-09
Hummm.......there was also a new audio package for the problem that I got from launchpad at one time as well.  When I had to reinstall I just went with the boot option instead.  Sorry I couldn't be of more help.

---

### Post by squakie on 2014-01-09
Try this link:

[https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)

and select the newest one for 13.10.

This patches the alsa sound and is what I used initially to get mine.  You still need to have the radeon.sound=1 in the grub files when you use this.  

When it all installed, reboot, then click on the sound icom on the top bar and click on sound settings to see if HDMI shows then.

---

### Post by catman915 on 2014-01-10
I,m not really linux literate. How would I install the item from the link you provided. Thanks

---

### Post by catman915 on 2014-01-10
Problem solved:) I was poking around and went to "Software & Updates/additional drivers" I changed the selection to one of the "fglrx" options. after that I did a system update before I rebooted and checked the audio settings so I'm not sure if it was the change or update or both but I now have audio. I appreciate your patience and assistance. Thanks again

---

### Post by squakie on 2014-01-11
Yeah, with AMD/ATI video it helps to load either flgrx or flgrx-updates, depending on the card.  Without that it wouldn't know about the HDMI output.  I didn't even think about it being something that simple for you - sorry!

Glad you got it all figured out and it's working for you!  Good job!

---

### Post by catman915 on 2014-01-11
No problem, I appreciate the help. Besides even a blind hog will find an acorn once in awhile :)

---

