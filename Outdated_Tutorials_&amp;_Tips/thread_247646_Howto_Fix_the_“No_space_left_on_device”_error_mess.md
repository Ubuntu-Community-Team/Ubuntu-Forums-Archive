---
title: "Howto Fix the “No space left on device” error message and Install the Spca5xx driver"
date: 2006-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by vodunvibe on 2006-08-30
[COLOR="Sienna"]**[SIZE="4"]Spca5xx[/SIZE]**[/COLOR]
The spca5xx driver included in the Dapper Drake (6.06) Ubuntu kernel works out of the box for most people, as it has been the case for myself until recently when I tried using my Webcam on an my other computers.

Unfortunately for some, trying to use their camera with the spca5xx driver when other USB devices are present on the same host controller bus as the camera, the following error appear: 
[B]No space left on device
can't open /dev/video0: No space left on device.[/B]

I have a Logitech QuickCam Communicate STX and an hp USB Multimedia Cordless Kit with a wireless keyboard and wireless mouse connected to the same host controller as my camera which. I also had the same error message as a result of this configuration.

The spca5xx driver supports a variety of cameras. For a full list of supported cameras, take a look at [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

[COLOR="Sienna"]**[SIZE="4"]Problem[/SIZE]**[/COLOR]
**When other USB devices are present on the same host controller bus as the camera, the bandwidth requirements of the spca5xx driver are not being met**, with some hardware configurations. **The spca5xx driver is asking for more bandwidth than is available** which results in the following error messages:

[B]No space left on device
can't open /dev/video0: No space left on device.[/B]

There is a very good howto for the Spca5xx driver at [https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)
if you haven't encountered the “No space left on device” error message.

[COLOR="Sienna"]**[SIZE="4"]Solutions[/SIZE]**[/COLOR]
There are multiple solutions which will work depending on your hardware configuration.
**Please be advised that it is best to connect the camera directly to the motherboard and not use a USB HUB.**

The only solution which worked in my particular situation, was to dig into the spca5xx source code ([spca5xx-20060501]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz")) and modify it by adding a fix, due to the fact that no matter which USB port I used, my camera always appeared on the same host controller bus as my USB keyboard and mouse.

**If you've already unsuccessfully shuffled your USB devices from port to port, you might want to skip ahead to Solution 2 and compile and install the modified spca5xx source code.**
[COLOR="Sienna"][B][LIST=1]
[*]Solution 1 - Put the camera on a separate USB host controller bus.
[*]Solution 2 - Compile and install the [modified spca5xx source code]("http://ubuntuforums.org/attachment.php?attachmentid=15350&stc=1&d=1157487906").
[*]Solution 3 - Buy an separate USB controller card. (This is a last resort solution which I wanted to avoid at all cost.)
[/LIST][/B][/COLOR]
[COLOR="Sienna"]**[SIZE="4"]Solution 1 - Put the camera on a separate USB host controller bus[/SIZE]**[/COLOR]
Try to put the camera on a separate USB host controller bus with no other devices on it.
(Assuming you don't have a USB keyboard and USB mouse. If you do skip to the next section)
[LIST=1]
[*]Unplug all other USB devices from your computer, leaving only the camera.
[*]If the camera works, then you need to figure out which USB ports are connected to which controller. You need to use your other USB devices after all. Experiment by connecting your other USB devices one by one to another USB port and see if the camera still works. If the camera stops working after connecting a device it means that the port you just used is on the same USB host controller bus as you camera.
[*]If after trying different combination of USB ports, you are not successful, try one of the following solutions.
[/LIST]

[COLOR="Sienna"]**[SIZE="4"]Solution 1 - Put the camera on a separate USB host controller bus (USB keyboard and USB mouse)[/SIZE]**[/COLOR]
Try to put the camera on a separate USB host controller bus with no other devices on it.
(If you can find a set PS/2 keyboard and mouse, try the above solution if not continue)
[LIST=1]
[*]Unplug all other USB devices from your computer, leaving only the camera and USB keyboard or only the camera and USB mouse, not both.
[*]If the camera doesn't work, experiment by connecting the camera to another USB port. Try all the other ports until you find one that works.
[*]If the camera works, then you need to figure out which USB ports are connected to which controller. You need to use your other USB devices after all. Experiment by connecting your other USB devices one by one to another USB port and see if the camera still works. If the camera stops working after connecting a device it means that the port you just used is on the same USB host controller bus as you camera.
[*]If the camera still doesn't work, please do not despair. Try the following solution.
[/LIST]

[COLOR="Sienna"]**[SIZE="4"]Solution 2 - Compile the modified spca5xx source code.[/SIZE]**[/COLOR]
The fix works by gradually lowering the bandwidth requirements of the driver (spca5xx-20060501) and  works even when other USB devices are present on the same host controller bus as the camera. 
**Then same method can also be used to resolve the same issue on the qc-usb QuickCam Express Driver.**

The new driver will be installed at this location (kernel 2.6 +): /lib/modules/`uname -r`/kernel/drivers/media/video/spca5xx/
The new driver will be installed at this location (kernel 2.4): /lib/modules/`uname -r`/kernel/drivers/usb/

**Please use one of the following 3 options:**
[COLOR="Sienna"][B][LIST=1]
[*]Automated Installation Script
[*]Manual Installation
[*]Patch
[/LIST][/B][/COLOR]

[COLOR="Sienna"]**[SIZE="4"]Automated Installation Script[/SIZE]**[/COLOR]
[B][LIST=1]
[*][Download the modified spca5xx source code]("http://ubuntuforums.org/attachment.php?attachmentid=15350&stc=1&d=1157487906") and save it on your desktop.
[*][Download the script]("http://ubuntuforums.org/attachment.php?attachmentid=15348&stc=1&d=1157486121") or copy and paste it in a new file and save it on your desktop.
[*]If you downloaded the [script]("http://ubuntuforums.org/attachment.php?attachmentid=15348&stc=1&d=1157486121") extract it from the archive using:
```
tar xfvz  spca5xxvodunvibeFixScript.tar.gz
```
[*]Execute the script on your desktop or in the same directory as the archive spca5xx-20060501vodunvibeFix.tar.gz
```
./spca5xxvodunvibeFix
```
[/LIST][/B]
```
#!/bin/sh
#spca5xxvodunvibeFix
#
# This Script to automatically installs spca5xxvodunvibeFix
#
## Exit if any command does not complete successfully.
#set -o errexit
#trap 'echo "The previous command did not complete successfully. "' ERR
echo "This script will extract and install spca5xx-20060501vodunvibeFix.tar.gz"
echo -e "\nThe following will also be downloaded and installed:"
echo "linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc"
echo "This script has been tested on Ubuntu Breezy Badger (5.10) and Dapper Drake (6.06)."
echo -e "\nPress enter to continue. CTRL-C to abort"
read
if grep -q "5.10" /etc/issue ; then
  sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4 
  export CC=gcc-3.4
else
  sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc
fi

KERNEL_VERSION=`uname -r`
MODULE_INSTALLDIR=/lib/modules/$KERNEL_VERSION/kernel/drivers/media/video/spca5xx
if [ -d /lib/modules/`uname -r`/build ]
then
    echo "The link Exists"
else
    echo "Creating link"
    ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
fi
#Move the modified spca5xx source code from your home directory to /usr/src
cd /usr/src
sudo mv ~/Desktop/spca5xx-20060501vodunvibeFix.tar.gz .
#Extract it from the archive:
sudo tar xfvz spca5xx-20060501vodunvibeFix.tar.gz
cd spca5xx-20060501vodunvibeFix
#Compile the spca5xx source code
sudo make clean
sudo make
#Remove the old driver from memory
sudo modprobe -r spca5xx
echo -e "\nBacking up current spca5xx.ko kernel module\n"
#Backup the current spca5xx.ko kernel module
sudo cp -p $MODULE_INSTALLDIR/spca5xx.ko $MODULE_INSTALLDIR/spca5xx.ko.`date -Iseconds`
#Install the new driver at this location /lib/modules/`uname -r`/kernel/drivers/media/video/spca5xx/
sudo make install
#Load the new driver
sudo modprobe spca5xx
#Check dmesg and the system logs for errors
dmesg
echo spca5xxvodunvibeFix Finished!
read

```


[COLOR="Sienna"]**[SIZE="4"]Manual Installation[/SIZE]**[/COLOR]

[LIST=1]
[*]**Download the necessary packages.**
To compile the drivers we need to make sure that the following packages are installed from the Ubuntu repositories:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc
```

If you are using Ubuntu Breezy Badger (5.10) you need gcc 3.4:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
export CC=gcc-3.4
```
**[*]Create a link to the kernel source if it does not exist.**
```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```
[B][*][Download the modified spca5xx source code]("http://ubuntuforums.org/attachment.php?attachmentid=15350&stc=1&d=1157487906") and save it on your desktop.

[*]Move the modified [spca5xx-20060501vodunvibeFix.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=15350&stc=1&d=1157487906") from your home directory to /usr/src[/B]
```
cd /usr/src
sudo mv ~/Desktop/spca5xx-20060501vodunvibeFix.tar.gz .
```
**[*]Extract the files from the archive.**
```
sudo tar xfvz spca5xx-20060501vodunvibeFix.tar.gz
```
**[*]Enter the directory.**
```
cd spca5xx-20060501vodunvibeFix
```
**[*]Compile the spca5xx source code.**
```
sudo make clean
sudo make
```
**[*]Remove the old driver from memory.**
```
sudo modprobe -r spca5xx
```
**[*]Backup the current spca5xx.ko kernel module.**
```
sudo cp -p /lib/modules/`uname -r`/kernel/drivers/media/video/spca5xx/spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/media/video/spca5xx/spca5xx.ko.`date -Iseconds`
```
**[*]Install the new driver at this location:** /lib/modules/`uname -r`/kernel/drivers/media/video/spca5xx/
```
sudo make install
```
**[*]Load the new driver.**
```
sudo modprobe spca5xx
```
**[*]Check dmesg and the system logs for errors. **
```
dmesg
tail -f /var/log/syslog
```
**[*]Enjoy your webcam.**
[/LIST]

[COLOR="Sienna"]**[SIZE="4"]Patch[/SIZE]**[/COLOR]
The more experienced users can use the following [patch]("http://ubuntuforums.org/attachment.php?attachmentid=15349&stc=1&d=1157486121") and perform a manual installation.

To apply the patch from your current working directory, with a subdirectory called spca5xx-20060501 use: 
```
patch -p0 < spca5xx-20060501-vodunvibe-Nospaceleftondevice.patch
```

To apply the patch, in the spca5xx-20060501 directory use: 
```
patch -p1 < spca5xx-20060501-vodunvibe-Nospaceleftondevice.patch
```

This patch is currently against the [spca5xx-20060501]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz") source.
```

diff -urN spca5xx-20060501.orig/drivers/usb/spca5xx.c spca5xx-20060501/drivers/usb/spca5xx.c
--- spca5xx-20060501.orig/drivers/usb/spca5xx.c	2006-04-29 11:38:07.000000000 -0400
+++ spca5xx-20060501/drivers/usb/spca5xx.c	2006-09-05 13:19:04.000000000 -0400
@@ -1574,6 +1574,66 @@
       spca50x->funct.stopN(spca50x);
 }
 
+
+/**********************************************************************
+* spcaReducePacketSize
+* Function Fixes the bandwidth problem that occurs
+* when other USB devices are on the same host controller bus as the
+* camera by gradually lowering the bandwidth requirements of the driver.
+* It works even when other USB devices are present on the same
+* host controller bus as the camera. 
+*
+* Problem
+* When other USB devices are present on the same host controller
+* bus as the camera, the bandwidth requirements of the spca5xx driver
+* are not being met. The spca5xx driver is asking for more bandwidth
+* than is available which results in the following error messages:
+*
+* No space left on device
+* can't open /dev/video0: No space left on device.
+* usb_submit_urb(0) ret -28
+*
+* 
+* Many thanks to all the wonderful people contributing to this project.
+*
+* Great work!
+* vodunvibe [AT] NO@SPAM.PLEASE yahoo DOT com
+* 2006-08-27
+* 
+***********************************************************************/
+static int spcaReducePacketSize(struct usb_spca50x *spca50x, int n, int err)
+{
+    int size=896, fx, i;
+    err("spcaReducePacketSize: vodunvibe - The usb_submit_urb(%d) transfer request submission failed - You probably have another device sharing the same USB Host Controller Bus as your camera. Try using another USB port, on a different host controller bus.", n);
+    while (err == -ENOSPC && size >= 0) {
+	    err("spcaReducePacketSize: vodunvibe - Lowering the bandwidth requirements - New packet size (%d) ", size);
+        spca50x_set_packet_size(spca50x, size);
+    	spca50x->sbuf[n].urb->transfer_buffer_length = spca50x->packet_size * FRAMES_PER_DESC;
+    	for (fx = 0; fx < FRAMES_PER_DESC; fx++) {
+    	    spca50x->sbuf[n].urb->iso_frame_desc[fx].offset = spca50x->packet_size * fx;
+    	    spca50x->sbuf[n].urb->iso_frame_desc[fx].length = spca50x->packet_size;
+    	}
+        size-=128;
+#if LINUX_VERSION_CODE > KERNEL_VERSION(2,5,41)
+    	err = usb_submit_urb(spca50x->sbuf[n].urb, GFP_KERNEL);
+#else
+    	err = usb_submit_urb(spca50x->sbuf[n].urb);
+#endif
+    }
+
+	if (!err) {
+      for (i = 0; i < SPCA50X_NUMSBUF; i++) {
+    	spca50x->sbuf[i].urb->transfer_buffer_length = spca50x->packet_size * FRAMES_PER_DESC;
+    	for (fx = 0; fx < FRAMES_PER_DESC; fx++) {
+    	    spca50x->sbuf[i].urb->iso_frame_desc[fx].offset = spca50x->packet_size * fx;
+    	    spca50x->sbuf[i].urb->iso_frame_desc[fx].length = spca50x->packet_size;
+    	}
+      }
+    }
+    return err;
+}
+
+
 static int spca50x_init_isoc(struct usb_spca50x *spca50x)
 {
 
@@ -1649,7 +1709,15 @@
 #endif
 	if (err) {
 	    err("init isoc: usb_submit_urb(%d) ret %d", n, err);
-	    return err;
+	    if (err == -ENOSPC) {
+	        err = spcaReducePacketSize(spca50x, n, err);
+        	if (err) {
+	            err("init isoc: After spcaReducePacketSize - usb_submit_urb(%d) ret %d", n, err);
+         	    return err;
+        	}
+	    }else{
+	        return err;
+	    }
 	}
     }

``` 

Many thanks to all the wonderful people contributing to this project.

---

### Post by tripmix on 2006-09-01
This did not work for me... Same camera, same error... Only difference is I'm on debian... But thx alot for trying, maybe someone else has better luck

---

### Post by zumbi on 2006-09-02
Didnt work for me too same error ... =/ no problem , ty for the help anyway, i thing i gonna buy other usb card , before die trying fix this thing!

---

### Post by Anduu on 2006-09-02
Man where was this how to last week :p

I wasted a couple hours trying to get mine to work before I accidentally discovered that switching some devices around fixed my troubles ;)

---

### Post by vodunvibe on 2006-09-02
Anduu! I'm glad you're out of the woods;)
tripmix, zumbi:
I'm sorry it didn't work for you. I know how frustrating this issue can be.  I would like to help.
Can you please post the output from dmesg?
```
dmesg
```

Thanks

---

### Post by ConiKost on 2006-09-03
Hi!

Thank you!

Your modifed driver works here fine.

What did you chanced?

Will you provide updated driver in the future?

---

### Post by vodunvibe on 2006-09-03
You're welcome ConiKost. I'm glad the modified driver works for you.:wink: 

As for what I changed, the code works by gradually throttling back the bandwidth used by the driver, in a way that minimizes the impact on the video image quality.
If you notice that the video image quality has been severely affected, it would imply that the USB devices are seriously taxing the USB bus.

Whenever I make a stable change to the code, I'll make an updated driver available until the code is suitable for integration in the spca5xx project.

If the modified driver works for anyone else, please let me know.:) 
If not, can you please post the output from dmesg and give some information about your hardware configuration?

Thanks

---

### Post by ConiKost on 2006-09-03
Hi!
I hope your modification will be in the future in the spca5xx driver ;)

I am using it under Gentoo!

I hope if its ok, that i submited an ebuild with your Patch ->
[http://bugs.gentoo.org/show_bug.cgi?id=146124](http://bugs.gentoo.org/show_bug.cgi?id=146124)

But I got to say, that the Image Quality is eactly the same!

Did you posted your Patch on the spca5xx mailing lists?

---

### Post by ConiKost on 2006-09-03
Hi!

I want to submit you Source in Gentoo Portage.

See here -> [http://bugs.gentoo.org/show_bug.cgi?id=146124](http://bugs.gentoo.org/show_bug.cgi?id=146124)

They would like to have an patch against the offical source.

Is that possible, that you could do this?

---

### Post by vodunvibe on 2006-09-04
Hi!

Sure, it's o.k. You can submit my source in Gentoo Portage. All in the spirit of sharing.
The more I can help the better.
I'm also glad that the image quality stayed the same.

I'm currently reviewing the code and will soon have a patch file ready, which will be posted here and on the spca5xx mailing lists. For everyone to use freely, without restrictions.

Thanks.

---

### Post by ConiKost on 2006-09-05
Thanks!

Waiting for your patch :)

---

### Post by vodunvibe on 2006-09-05
I posted the patch a few hours ago at the end of the how to;)
The patch alone is in [spca5xx-20060501-vodunvibe-Nospaceleftondevice.patch.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=15349&stc=1&d=1157486121")
Here are the instructions followed by the patch.

Thanks:)


Subject: [PATCH] spca5xx patch for “No space left on device”  error message

This patch Fixes the bandwidth problem that occurs when other USB devices
are on the same host controller bus as the camera by gradually lowering the
bandwidth requirements of the driver.

When the patch is applied,  spca5xx drivers works even when other USB devices
are present on the same host controller bus as the camera.

This patch is currently against the spca5xx-20060501 source.

To apply the patch from your current working directory, with a subdirectory
called spca5xx-20060501 use: 
patch -p0 < spca5xx-20060501-vodunvibe-Nospaceleftondevice.patch

To apply the patch, in the spca5xx-20060501 directory use: 
patch -p1 < spca5xx-20060501-vodunvibe-Nospaceleftondevice.patch

Bandwidth Problem details:
 When other USB devices are present on the same host controller
 bus as the camera, the bandwidth requirements of the spca5xx driver
 are not being met. The spca5xx driver is asking for more bandwidth
 than is available which results in the following error messages:

 No space left on device
 can't open /dev/video0: No space left on device.
 usb_submit_urb(0) ret -28


Thanks,
vodunvibe


diff -urN spca5xx-20060501.orig/drivers/usb/spca5xx.c spca5xx-20060501/drivers/usb/spca5xx.c
--- spca5xx-20060501.orig/drivers/usb/spca5xx.c	2006-04-29 11:38:07.000000000 -0400
+++ spca5xx-20060501/drivers/usb/spca5xx.c	2006-09-05 13:19:04.000000000 -0400
@@ -1574,6 +1574,66 @@
       spca50x->funct.stopN(spca50x);
 }
 
+
+/**********************************************************************
+* spcaReducePacketSize
+* Function Fixes the bandwidth problem that occurs
+* when other USB devices are on the same host controller bus as the
+* camera by gradually lowering the bandwidth requirements of the driver.
+* It works even when other USB devices are present on the same
+* host controller bus as the camera. 
+*
+* Problem
+* When other USB devices are present on the same host controller
+* bus as the camera, the bandwidth requirements of the spca5xx driver
+* are not being met. The spca5xx driver is asking for more bandwidth
+* than is available which results in the following error messages:
+*
+* No space left on device
+* can't open /dev/video0: No space left on device.
+* usb_submit_urb(0) ret -28
+*
+* 
+* Many thanks to all the wonderful people contributing to this project.
+*
+* Great work!
+* vodunvibe [AT] [email]NO@SPAM.PLEA[/email]SE yahoo DOT com
+* 2006-08-27
+* 
+***********************************************************************/
+static int spcaReducePacketSize(struct usb_spca50x *spca50x, int n, int err)
+{
+    int size=896, fx, i;
+    err("spcaReducePacketSize: vodunvibe - The usb_submit_urb(%d) transfer request submission failed - You probably have another device sharing the same USB Host Controller Bus as your camera. Try using another USB port, on a different host controller bus.", n);
+    while (err == -ENOSPC && size >= 0) {
+	    err("spcaReducePacketSize: vodunvibe - Lowering the bandwidth requirements - New packet size (%d) ", size);
+        spca50x_set_packet_size(spca50x, size);
+    	spca50x->sbuf[n].urb->transfer_buffer_length = spca50x->packet_size * FRAMES_PER_DESC;
+    	for (fx = 0; fx < FRAMES_PER_DESC; fx++) {
+    	    spca50x->sbuf[n].urb->iso_frame_desc[fx].offset = spca50x->packet_size * fx;
+    	    spca50x->sbuf[n].urb->iso_frame_desc[fx].length = spca50x->packet_size;
+    	}
+        size-=128;
+#if LINUX_VERSION_CODE > KERNEL_VERSION(2,5,41)
+    	err = usb_submit_urb(spca50x->sbuf[n].urb, GFP_KERNEL);
+#else
+    	err = usb_submit_urb(spca50x->sbuf[n].urb);
+#endif
+    }
+
+	if (!err) {
+      for (i = 0; i < SPCA50X_NUMSBUF; i++) {
+    	spca50x->sbuf[i].urb->transfer_buffer_length = spca50x->packet_size * FRAMES_PER_DESC;
+    	for (fx = 0; fx < FRAMES_PER_DESC; fx++) {
+    	    spca50x->sbuf[i].urb->iso_frame_desc[fx].offset = spca50x->packet_size * fx;
+    	    spca50x->sbuf[i].urb->iso_frame_desc[fx].length = spca50x->packet_size;
+    	}
+      }
+    }
+    return err;
+}
+
+
 static int spca50x_init_isoc(struct usb_spca50x *spca50x)
 {
 
@@ -1649,7 +1709,15 @@
 #endif
 	if (err) {
 	    err("init isoc: usb_submit_urb(%d) ret %d", n, err);
-	    return err;
+	    if (err == -ENOSPC) {
+	        err = spcaReducePacketSize(spca50x, n, err);
+        	if (err) {
+	            err("init isoc: After spcaReducePacketSize - usb_submit_urb(%d) ret %d", n, err);
+         	    return err;
+        	}
+	    }else{
+	        return err;
+	    }
 	}
     }

---

### Post by ConiKost on 2006-09-06
Thanks!

Patch is working w/o any Problems ;)

---

### Post by quik77 on 2006-09-11
tried your fix after a number of other tries at a solution, however I am on 64bit ubuntu if that makes a difference.

was trying to get a Creative PD1170 (notebook webcam) to work with Kopete and I followed their instructio0ns in the wiki.  That particular howto tells me first to install the drivers, which I followed This howto for, and  than to run xawtv to check if it works and I get back this

> $ xawtv -d ot i /dev/video This is xawtv-3.94, running on Linux/x86_64 (2.6.15-26-amd64-k8)
can't open /dev/video0: No space left on device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No space left on device
v4l2: open /dev/video0: No space left on device
v4l: open /dev/video0: No space left on device
no video grabber device available


so I think its the same problem...  

anyone got a clue for me? cause I got nothing lol

---

### Post by vodunvibe on 2006-09-15
Hi!

Your Creative PD1170 does work with the spca5xx driver.
I've also tested the fix on 64bit ubuntu and it doesn't make a difference.

Can you please post the output from the following? (After you unplug your camera, then plug back in and try to use it)
```
dmesg
ls -la /dev/video*
```
Do you have a TV tuner card or any other video devices?
I would like to help you diagnose and fix the problem.

Thanks.

---

### Post by iyeo on 2006-09-23
Sweet!  This worked kinda.  I now have working video in camorama, xawtv, and spcaqui, but ekiga still cannot open video0.  It does, however, now recognize the cam during detect.  How can I fix ekiga?  Or should I scrap ekiga and get another program?  What's a good alternative which lets me chat on all networks and has video?  

Also, spcagui for some reason displays with transparency!!  Unless I have something dark in the background, it's very hard to see.  If I switch the video mode to yuv, the video display portion will come in without transparency, but the menu, like all non-yuv modes, is always tranparent.  I suspect it might have to do with me running compiz and xgl.

I'm running Dapper64 on AMD64x2 with the STX.

---

### Post by tripmix on 2006-10-07
Saw your guide was a little updated since last I was here so I tried applying the patch manualy and now it works fine. Thanks alot :)
I have no idea why it didnt work the last time tough.

---

### Post by peterl on 2006-10-22
HowTo worked well for me too. Just one problem...

Having followed your advice, my webcam now appears to have its brightness turned up to maximum, and the sliders in camorama don't seem to be making a difference (that is, they're on their lowest values). Is there a config file I can alter manually somewhere that allows me to set parameters like these?

Webcams with linux are still a bit of a mystery to me!

Thanks,
Peter.

p.s., here's my dmesg when i unplugged-replugged the camera:

[ 1491.054960] usb 2-3: USB disconnect, address 2
[ 1491.055260] drivers/usb/media/spca5xx/spca5xx-main.c: usb_submit_urb() ret -1 9
[ 1491.055267] drivers/usb/media/spca5xx/spca5xx-main.c: usb_submit_urb() ret -1 9
[ 1504.578309] usb 2-3: new full speed USB device using ohci_hcd and address 3
[ 1504.684451] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera foun d. SONIX sn9c101 + Ov7630

---

### Post by loko on 2006-10-27
hi, 

thanks for the howto but i get some errors:

this is when i enter dmsg:

```
[17183315.396000] usbcore: registered new driver spca5xx
[17183315.396000] /home/user/spca5xx-20060501vodunvibeFix/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17183411.888000] usbcore: deregistering driver spca5xx
[17183411.888000] /home/user/spca5xx-20060501vodunvibeFix/drivers/usb/spca5xx.c: driver spca5xx deregistered
[17183425.200000] Linux video capture interface: v1.00
[17183425.204000] usbcore: registered new driver spca5xx
[17183425.204000] /home/user/spca5xx-20060501vodunvibeFix/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered

```


but if i start camorama (as user or root)  get the error:

```
could not connect to video device (/dev/video0). please check connection.
```

i cannot unplug the camera, because it is built-in into the laptop.

what is wrong?

---

### Post by CyberAngel on 2006-10-28
voduvibe you are my man :KS :) :D 

I had this problem over a year now and I had post the same question twice (first for breezy, then for dapper) but no answer from anyone!!

Now I switched to edgy eft and I searched the forums again and I found your post that fixed the problem instantly :)

Just one question. I use spcaview to check my camera and the image is sooooooo dark that you can`t even recognize objects.
Do you know how can I adjust my brightness and contrast settings because I had never act with a webcam again.

Anyway thank you so much :)

---

### Post by bodhi.zazen on 2006-10-31
Nice How-to voduvibe

**Love the avatar**

This thread has been added to the UDSF wiki.

[Howto Fix the “No space left on device” error message and Install the Spca5xx dri](http://doc.gwos.org/index.php/Fix_No_space_left_on_device_error_message_and_Install_the_Spca5xx_driver)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Balaam's Miracle on 2006-12-13
Vodunvibe, i love you!

I finally have my Logitech ClickSmart 510 working.

Well, it's working partially. I have recently moved from Windows to Ubuntu (6.10) and in Windows a lot more features of this camera are detected (i don't think it's you fault, just saying what i'm missing).
Right now, the camera is working only as a webcam without sound.
However, it has a built-in microphone, is a digital camera and none of those features are detected in Ubuntu. Now i have a bunch of pics on the cam that i can not import...

Ah well, maybe a later version of the driver will detect it all..

P.S. The image is very dark and the colours are exaggerated, any idea how i can change that?

---

### Post by CyberAngel on 2006-12-14
> **Balaam's Miracle said:**
> .......
P.S. The image is very dark and the colours are exaggerated, any idea how i can change that?

I have the same problem on a Webcam Vista :(

---

### Post by Syock on 2006-12-15
If I want to apply the same patch to the newer GSPCA drivers, what changes should I make to the diff? AFAIK the latest is v1-01.00.10 released 05-Dec-2006.

EDIT : Sorry about my blunder. It seems gspca already adrressed this issue. I failed to realize that I wasn`t installing gspca properly.

---

### Post by Balaam's Miracle on 2006-12-22
Just a quicky, the first image is what my webcam image looks like with all sliders in their default position ( 128 ).
The second one is when i've made the following adjustments in Camorama:
- Contrast = 46
- Brightness = 227
- Color = 16
The hue and whitebalance sliders don't seem to do anything.
Oh, and i've applied the Color Correction filter, now my curtains are red, like they are supposed to be :-)

Hopefully this could help improving the drivers.

---

