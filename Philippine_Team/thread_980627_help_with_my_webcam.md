---
title: "help with my webcam"
date: 2008-11-13
forum: Philippine Team
---

### Post by Script Warlock on 2008-11-13
i got my bagong neo elan at nilagyan ko ng ubuntu 8.10 kaso hindi gumana ang built-in webcam kahit na sinubukan ko to thread [http://ubuntuforums.org/showthread.php?t=593231](http://ubuntuforums.org/showthread.php?t=593231)

pero wala pa rin nangyari eto pala output ng dmesg ko 

uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).
[15753.291625] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).
[15753.459228] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).
[15753.464961] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.

at eto na man sa lsusb

whitehat@whitehat-laptop:~$ lsusb
Bus 007 Device 003: ID 5986:0202 Acer, Inc 
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

try ko na sa cheese at lucview or whatever pero wla pa rin display...ano kaya problema?:confused:

---

### Post by loell on 2008-11-13
heto.. try mo 'to

[http://ubuntuforums.org/showpost.php?p=5247345&postcount=3]("http://ubuntuforums.org/showpost.php?p=5247345&postcount=3")

---

### Post by killer_d76 on 2008-11-14
having issue with webcam driver too.. boyet if you were able to make it work give me a heads up so i could try it as well hehehe, my webcam has not been working since hardy eh. :(

---

### Post by Script Warlock on 2008-11-15
unfortunately walang bisa pra sa akin ang link na to  [http://ubuntuforums.org/showpost.php?p=5247345&postcount=3](http://ubuntuforums.org/showpost.php?p=5247345&postcount=3)

pero eto yung mas epiktibo para sa webcam ko sa neo elan:

sudo apt-get install build-essential libsdl1.2-dev libpt-plugins-v4l2 subversion
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo modprobe -r uvcvideo
sudo make install
sudo modprobe uvcvideo
cd ..
wget [http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz)
tar -zxvf luvcview-20070512.tar.gz
cd luvcview-20070512/
make

check your webcam if it is working with this:

./luvcview

and mine is working...

:guitar:

---

### Post by killer_d76 on 2008-11-15
good to hear your webcam is working now!.. i'll give this a shot first.. (my webcam did not worked since Hardy :( )

---

### Post by Script Warlock on 2008-11-16
ano pala webcam mo

---

