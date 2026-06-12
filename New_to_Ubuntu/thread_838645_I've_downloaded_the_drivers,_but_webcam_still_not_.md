---
title: "I've downloaded the drivers, but webcam still not working!"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by stropyboy11 on 2008-06-23
I was discussing this before on a seperate thread, but I fell asleep. Grr. Anyway, I downloaded the drivers for my webcam (built in to my HP DV6000T laptop), but the webcam still isn't working. I know the drivers are good because I had my webcam working before I had to get a new harddrive. Any suggestions?

-Stropko

---

### Post by rogier.de.groot on 2008-06-23
Webcam driver for *linux* what weird parallel universe did you just wake up in? Seriously though: give us some more details to work with.

---

### Post by markbuntu on 2008-06-23
Are you using V4l or V4l2?

Some cams will not work with V4l2 but will with V4l.

---

### Post by Kingsley on 2008-06-23
Hey, I have the same laptop as you. My webcam has been working without any tweaking since the release of Gutsy.

Maybe the steps in this **[HOWTO]("http://ubuntuforums.org/showthread.php?t=512059")** will work.

**Sonix/Microdia Webcam**
 Open a console and enter: ```
lsusb
``` If it looks similar to the following ```
Bus 002 Device 002: ID 0c45:62c0 Microdia
``` 1) Install subversion from the repos. Open Terminal type this: ```
sudo apt-get install subversion
``` 2) In Terminal enter this:
            ```
svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
            cd trunk/
            gedit Makefile
```        3) Change the following in the Makefile:
            INSTALL_MOD_DIR := usb/media
            to
            INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo

        4) Save it and close. In Terminal type:
            ```
make
            sudo make install
            sudo modprobe uvcvideo
            gstreamer-properties
```        5) Under VIDEO, select v4l2 and choose USB 2.0 for device.

---

### Post by adam_kimber on 2008-06-23
Hi. 

what does ```
lsusb
``` give you? The webcam is probably a hard wired usb device. 

If it is then its probably the Microdia one,have a look at this page and scroll down to the Mircodia webcam bit. [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

---

### Post by stropyboy11 on 2008-06-23
My apologies for lack of information. All the grusome details are located here:

[http://ubuntuforums.org/showthread.php?t=838080](http://ubuntuforums.org/showthread.php?t=838080)

---

### Post by stropyboy11 on 2008-06-23
Can someone please help?

---

### Post by stropyboy11 on 2008-06-23
Ok, sorry for the delay, but I got distracted. It's a Ricoh Webcam > Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd 


---

### Post by barney385 on 2008-06-23
Just install cheese and it's dependencies.

It's in the repositories...


:smile:

---

### Post by stropyboy11 on 2008-06-23
I installed cheese from Synaptic, but it didn't say it needed any dependencies. When I try to open the program, I get colored bars (see pic).

Any suggestions?

---

### Post by stropyboy11 on 2008-06-23
...anyone? Please? This has been quite an ordeal...

---

### Post by adam_kimber on 2008-07-02
Not sure why cheese would work without the right driver. For the DV6000 you will either need one of the following drivers. Richoh or Microdia. 

As you have stated you need the ricoh driver and your lsusb confrims this 05ca:1810 is the device code for a Richoh Webcam. 

Get the latest driver from [Arakhne.org]("http://www.arakhne.org/spip.php?article50"). Just need to match the driver to the version (gutsy, hardy etc) and kernel (type uname -a to get that). Then look at that page and download. Also grab this package and install it [Deb File]("http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.0-2arakhne1_i386.deb")

PS Webcams and linux are a pain as most companies have not released any specs for the cameras or any source code for the drivers so people have had to make up a driver by fiddling.

PPS Run Ekiga (synaptic search shoudl give you that program if its not already installed) and see if it works there.

---

