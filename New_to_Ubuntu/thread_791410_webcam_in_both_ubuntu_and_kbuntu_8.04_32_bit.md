---
title: "webcam in both ubuntu and kbuntu 8.04 32 bit"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by ecrivain5 on 2008-05-12
Before I buy a new webcam. Can those of you that have webcams up and running without a lot of hassle please let me know the make and model (under £30 please)
I will be running either. Ubuntu 8.04 desktop (Gnome) 32 bit OR 
Ubuntu 8.04 desktop (KDE) 32 bit.
Sadly my present camera (an older version of logitech 5000pro) is not a happy bunny with Hardy:-)
Thanks guys as ever for you help
PS please don't direct me to the wiki site.
I really want to know those that ARE working now.=D>

---

### Post by spiderbatdad on 2008-05-12
Surprised to hear this cam is not working "out-of-the-box" for you. I have one of the ancient logitech cams called: Logitech quick cam express." It has always worked perfectly. Could it be that the application you are trying to use has some unmet dependencies? For example, try to use kopete for video IM without Jasper installed.

There is some info here about getting your model working on the previous kernel, it is still a valid approach, and may help you, if you wish to try to get the cam you have working:[https://answers.launchpad.net/ubuntu/+question/3743](https://answers.launchpad.net/ubuntu/+question/3743)



> Make sure first you have all the tools for the job;

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential subversion

Once you have got all them you will need to use subversion to get the driver from the svn repo..

svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)

Then you need to compile and install

cd linux-uvc/linux-uvc/trunk
make
sudo make install

Plug the camera in and take a look at dmesg. It may [hopefully] give you the device listing for it... eg /dev/video1

Point your application at that device and see if it works.

---

