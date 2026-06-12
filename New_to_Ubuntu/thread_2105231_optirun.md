---
title: "optirun"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by quarkhirad on 2013-01-15
I just bought a new laptop a dell xps with the nvidia optimus technology i installed bumblebee using the following 

```

sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo apt-get install bumblebee 
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

```

I then restarted the computer. 

i then ran glxspheres. which gave me the following output 

> khirad@gini:~$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0xa1
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
59.722667 frames/sec - 66.650497 Mpixels/sec
59.792658 frames/sec - 66.728607 Mpixels/sec
khirad@gini:~$ 

I then ran optirun glxspheres. which gave me the following error

> khirad@gini:~$ optirun glxspheres 
[ 3172.011322] [ERROR]You've no permission to communicate with the Bumblebee daemon. Try adding yourself to the 'bumblebee' group
[ 3172.011421] [ERROR]Could not connect to bumblebee daemon - is it running?
khirad@gini:~$ 

if i run sudo optirun glxspheres. It gives me the following 

> khirad@gini:~$ sudo optirun glxspheres 
[sudo] password for khirad: 
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCIe/SSE2
132.378804 frames/sec - 147.734745 Mpixels/sec
137.626886 frames/sec - 153.591604 Mpixels/sec
134.352428 frames/sec - 149.937310 Mpixels/sec


Can someone explain the error and how to fix it.

---

