---
title: "IPWebcam not installing/working as android webcam"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by varunreeves on 2012-01-30
Hello everyone.I have ubuntu lucid lynx 10.04  with the latest updates with a windows xp sp3 dual boot.The laptop I use is inspiron 600m(old model , I know!).I have run into to some trouble and request advice. I have 2 android phones, the galaxy y and the galaxy note.I read online that I could use the galaxy y 2 MP back camera as a webcam and I tried this in windows using Ip webcam and was successful but was not able to do this in linux. I followed the websites mentioned below.The author for the script from website 1 below says that he was able to install it in 11.04 but I cannot get it to work in lucid lynx.The details are given below.

Websites used -- 
1.Ipwebcam---https://market.android.com/details?id=com.pas.webcam&hl=en 
2.For installing Ipwebcam packages for ubuntu --https://github.com/bluezio/ipwebcam-gst
3.v4l2loopback manual install --https://github.com/umlaeute/v4l2loopback

Steps and errors`--
Step 1. Installed Ipwebcam from site 1 abovein my android phone and checked.It works fine.

Step 2.After starting the server for Ipwebcam on my phone I get a local IP which I use in my laptop browser and use the port 8080 i.e I put this in my firefox address bar --http://192.168.2.5:8080/    --- .
I am directed to website 2 above to download the package and run the script "prepare-videochat.sh".I do as instructed but I get a pop up with the error message -- "The v4l2loopback kernel module is not installed or could not be loaded. I will try to install the kernel module using DKMS. If that doesn't work, please install v4l2loopback manually from github.com/umlaeute/v4l2loopback".I click "OK" on the pop up and the entire output I get is as follows -- 
```
varun@varun-laptop:~/Source file for android ph as webcam for skype and all/bluezio-ipwebcam-gst-c18a726$ ./prepare-videochat.sh 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2012-01-30 14:54:23--  http://ftp.us.debian.org/debian/pool/main/v/v4l2loopback/v4l2loopback-dkms_0.4.0-1_all.deb
Resolving ftp.us.debian.org... 128.30.2.36, 2001:500:61:28::70
Connecting to ftp.us.debian.org|128.30.2.36|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-01-30 14:54:24 ERROR 404: Not Found.
```

Step 3.On the webpage 2 itself I click on the v4l2loopback link and get to webpage 3 above.I download the package from there and store it somewhere ( it is not in /home but another partition /media/a/ in my laptop) and then try to run the "make" and the entire output is like this --
```
 
#make
Building v4l2-loopback driver...
make -C /lib/modules/`uname -r`/build M=/home/varun/Source file for android ph as webcam for skype and all/umlaeute-v4l2loopback-a303e20 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
make[1]: *** No rule to make target `file'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'
make: *** [v4l2loopback] Error 2

```

```

 sudo make
Building v4l2-loopback driver...
make -C /lib/modules/`uname -r`/build M=/home/varun/Source file for android ph as webcam for skype and all/umlaeute-v4l2loopback-a303e20 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
make[1]: *** No rule to make target `file'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'
make: *** [v4l2loopback] Error 2

```

I checked in synaptic and found that I have v4l2loopback-source as already installed but I cannot find any package called only v4l2loopback.What should I do next?

---

### Post by varunreeves on 2012-01-30
Would be wonderful if someone can reply to this.

---

