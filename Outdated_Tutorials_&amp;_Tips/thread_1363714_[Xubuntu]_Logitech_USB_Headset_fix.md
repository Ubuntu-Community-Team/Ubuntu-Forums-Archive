---
title: "[Xubuntu] Logitech USB Headset fix"
date: 2009-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Nyken on 2009-12-24
Logitech USB Headset [Xubuntu]

Went nuts for days trying to find this solution. Looked at 100 different pages and it felt like I was just screwing my system up more than it was already. Also, 100% of the tutorials and suggested fixes were tailored of Ubuntu, not Xubuntu, which make there be zero point of reference as to what apps to use to properly configure things. I was near to going back to Ubuntu (which my headphones worked flawlessly, even was in the process of  apt-getting Ubuntu-desktop when the fog cleared and I took one last shot.

Hope this will make it easier for at least 99% of you.

Backtracking through what I finally did, this is a series of steps that got my Logitech USB Headset working with Xubuntu 9.10. 

With Xubuntu 9.10, make sure you have the pulseaudio installed. Apparently Logitech USB headsets needs pulseaudio; guess there is an issue with ALSA, but I really don't know. none of the asoundconf-gtk stuff helped me a bit. ALSA see it, but I guess Gandalf is there with a burning sword screaming "You shall not pass!!" at it. 

Type "sudo apt-get install pulseaudio" and see if it brings up anything to install. It should list things like "gstreamer0.10-pulseaudio" and about 6 other libraries. Made sense to me when I first saw it, since I had zero volume with Totem. 

Next make sure you have Pulseaudio Volume Control installed in Applications > Multimedia. If not, install it with "sudo apt-get install pavucontrol" This package is important; a must-have for this to work.

With all the pulseaudio packages installed, you can open your Pulseaudo Volume Control applet. What's strange is that I was able to install it first - however it didn't work until I installed the pulseaudio packages . Said something about not being able to connect to server. Makes sense. This is what sat in the back of my mind and said that pulseaudio must be missing.

By Tab, these are the settings you will need to have:

Playback - leave alone.

Recording - Show: Hardware Output Devices 
                      Your Headset should be listed. Mine is called "Premium Stereo USB Headset 350 Digital Stereo
                      (IEC95,) so something akin to that. Leave it's settings alone, unless your need volume gain on your
                      mike.

Input - Show: All Except Monitors. 
            Again, your headset should be listed. Leave it's settings alone.

Configuration - Go to the box with your headset listed. Chose this profile - Digital Stereo (IEC95)  Output + Analog  
                           Input. You may have to adjust that one according to your model - not sure, but it's what's mine is set
                           to.

                           Internal Audio - Profile: Off. That finally routes everything sonic to your headset.


Hope that fixes your problem like it's fixed mine. Enjoy the music.

---

### Post by jpeddicord on 2009-12-28
Approved; thanks for your contribution to Tutorials & Tips!

---

### Post by stereo7 on 2010-05-06
Thank you !  pavucontrol - all I want!!! my usb logitech headset work perfect! :guitar:

---

