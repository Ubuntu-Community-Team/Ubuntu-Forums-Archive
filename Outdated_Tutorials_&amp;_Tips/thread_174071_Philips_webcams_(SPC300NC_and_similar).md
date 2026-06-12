---
title: "Philips webcams (SPC300NC and similar)"
date: 2006-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by maulattu on 2006-05-11
The linux kernel doens't support this kind of webcams, nor it has suited drivers. How it works???:confused: 

Take a look at [http://mxhaard.free.fr/](http://mxhaard.free.fr/)
you'll find suited drivers to install and configure such webcams (here there's a list of supported webcams: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)).

1) With the provided ubuntu kernel you will have the support of video devices, so let skip to step 3.

2) If you do not have the standard kernel, you must assure that your kernel supports  video devices. to check this:
```

cd /usr/src/linux
sudo make menuconfig

```
in the "Device drives" section select "Multimedia devices" and check if the 'Video for linux' is selected ('M'). If it is selected skip to step 3, else you must select it (space bar), recompile your kernel and reboot the pc (for the kernel copilation looks at the tseliot's recompilation kernel guide in this section).

3) Download [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
uncompress it and compile it (look at the INSTALL file, it requires sdl libraries):
```
make clean
make
sudo make install
```
plug the cam and type
```
sudo lsmod
```
and spca5xx should be load with videodev, if not, somethings goes wrong.

4) download [http://mxhaard.free.fr/spca50x/Download/spcaview-20051212.tar.gz](http://mxhaard.free.fr/spca50x/Download/spcaview-20051212.tar.gz)
uncompress it and install it
```
make
sudo make install
```

5) with the camera plugged type
```
spcaview -d /dev/video0 -f yuv
```
and you should see your image (to exit close the window).
note: with the philips webcam you will see flipped images, and 'till now i've never find a suitable method to see unflipped images (... a method exists: flip the camera :mrgreen: ).

With this guide your webcam will also work in kopete 8)

---

### Post by mkarnicki on 2008-03-25
You might want to check this thread, they mention flipping the philips cam: [http://ubuntuforums.org/showthread.php?t=262108&highlight=flip+cam](http://ubuntuforums.org/showthread.php?t=262108&highlight=flip+cam)

**EDIT:** sorry, that's not quite what you meant. If you know how to flip horizontally the SPC200NC Philips webcam, please let me know.

---

