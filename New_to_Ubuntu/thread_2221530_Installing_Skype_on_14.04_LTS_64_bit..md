---
title: "Installing Skype on 14.04 LTS 64 bit."
date: 2014-05-02
forum: New to Ubuntu
---

### Post by Toni_Vines on 2014-05-02
OK, having done a total purge of Skype I'm about to start again.
I'm aware that 
sudo apt-get install skype
will install but when I tried to install it last time I had no webcam working and no sound. I know my webcam is ok because it works in Cheese and the overall sound on this PC is good. I'd be very greatful for any pointers / help in achieving this successfully.
Thanking you,
Toni.

---

### Post by gifford on 2014-05-02
You might look this over first: [http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html](http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html)
The alternate method of install listed at the bottom might solve your problem. The -f will attempt to correct any broken dependencies.

---

### Post by Toni_Vines on 2014-05-02
Thanks Gifford, much appreciated.

---

### Post by Toni_Vines on 2014-05-02
OK, I have installed as per the advice given and I have sound but no video. Any help would be wonderful, cheers.
Toni.

---

### Post by gifford on 2014-05-02
Let's see what webcam you are using. Can you post the results of lsusb?

---

### Post by Toni_Vines on 2014-05-02
Here you go! 

toni@workstation:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 005 Device 005: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
toni@workstation:~$

---

### Post by gifford on 2014-05-02
Was the camera working for Skype in another version of Ubuntu?

---

### Post by Toni_Vines on 2014-05-02
Yes it was with a work-around! I've tried this work-around on here but it does nothing. Basically it was a line of code I had to put in the terminal and start Skype with that. Even then it wasn't great. It was fine until I conected with someone, then it started flashing. The person on the other end got a fine, constant picture but  mine was dreadful!

---

### Post by gifford on 2014-05-02
Your webcam may not be supported by Skype.
Here is a link:[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by Don_Tai on 2014-05-02
I had a couple of webcams that worked straight away in Cheese but did not work on Skype. You may need to switch your webcam, unfortunately.

---

