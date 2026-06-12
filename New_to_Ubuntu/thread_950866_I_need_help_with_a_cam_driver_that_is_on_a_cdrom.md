---
title: "I need help with a cam driver that is on a cdrom"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by thrasher6900 on 2008-10-17
I have a 'gfm' cam that windows cannot even pick up the drivers for without the cdrom.

Is there a way to install this driver from my cd rom and get it working?

I tried synaptic, but nothing worked right and it's kinda confusing and I don't want to install something that could mess something up. (I've done so trying to get s-video to work.  I ended up taking 3 hours trying to fix my resolution :oops: )

---

### Post by theevilhamster on 2008-10-17
have you tried installing wine?

---

### Post by gletob on 2008-10-17
Those drivers are usually for windows only could you give me the exact model number of the camera?

---

### Post by thrasher6900 on 2008-10-17
> **theevilhamster said:**
> have you tried installing wine?
It does not work on wine.  It freezes up. :(

---

### Post by thrasher6900 on 2008-10-17
> **gletob said:**
> Those drivers are usually for windows only could you give me the exact model number of the camera?It's a gfm brand and the model  # is ulq-902 . . ...I think.  The disk says ' Webcam ULQ-902 '

---

### Post by thrasher6900 on 2008-10-17
:confused:

---

### Post by gletob on 2008-10-18
istall this sometimes webcams are automatically supported by ubuntu
run it see if your cam comes up
sudo apt-get install luvcview

---

### Post by thrasher6900 on 2008-10-18
> **gletob said:**
> istall this sometimes webcams are automatically supported by ubuntu
run it see if your cam comes up
sudo apt-get install luvcviewIt didn't work.:(

This is what came up.

```
SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal
```

---

### Post by gletob on 2008-10-18
oops wrong program my bad

you can go ahead and remove luvcview by running:
sudo apt-get remove luvcview

Plug in your cam

Now install XAWTV by running:
sudo apt-get instal xawtv

now open it in Apps>Sound & Video>XAW TV

If your cam works the picture should come up

---

### Post by thrasher6900 on 2008-10-18
> **gletob said:**
> oops wrong program my bad

you can go ahead and remove luvcview by running:
sudo apt-get remove luvcview

Plug in your cam

Now install XAWTV by running:
sudo apt-get instal xawtv

now open it in Apps>Sound & Video>XAW TV

If your cam works the picture should come upwill this allow me to use other programs to record video?  It has a mic as well.

I cannot seem to get it to record and when I hit capture, it doesn't show the pic or tell me where it's going.

---

### Post by gletob on 2008-10-18
It should save pictures directly in you Home Folder if it's working in that program it should work with others

---

### Post by thrasher6900 on 2008-10-19
> **gletob said:**
> It should save pictures directly in you Home Folder if it's working in that program it should work with others
I cannot record video.

I either get an error or it's choppy.

Any other ideas?  Addons?  Libraries:confused:?

---

### Post by patrickballeux on 2008-10-19
To validate if you webcam works in Ubuntu, you can simply run this tools from a terminal of doing ALT-F2 (Run window...)

gstreamer-properties


Then look in the "Video" tab, at the bottom, you have setup for video capture.  Try with V4L or V4L2 with the test button.  You can also set the default webcam to use (If you have more than one).


As for sound, you shoule use "pavucontrol" (install from Synaptic) which will let you select your microphone webcam inside Pulseaudio server.  Once installed, run it from the terminal/ALT-F2 on look for it in the menu Application.  Opening the Volume Control, in the Capture Tab, you should see your soundcard capture and if detected, your webcam microphone.
This is where you can select Pulseaudio to use the default as being your microphone.

Let me know!

---

### Post by patrickballeux on 2008-10-19
> **thrasher6900 said:**
> I cannot record video.

I either get an error or it's choppy.

Any other ideas?  Addons?  Libraries:confused:?

Have you tried Cheese?

Also, you can play with Camstrean which is quite good to play with your webcam.

Using WebcamStudio for GNU/Linux, you could broadcast on Youtube/BlogTV/Ustream and Flash 10 and download the recorded video.

Me, to record locally, I use "gst-launch" (gstreamer) from the command line to capture sound and image into an OGG file.  I don't have access currently to the script as it is on another computer, but I post it as another way to capture.

Good luck!

---

### Post by Art2U on 2008-11-22
In WinXp, the driver for GFM webcam is install in the 
C:\Program Files\Vimicro\Vimicro USB PC Camera (ZS0211).
This makes me believe that the GFM webcam is indeed a Vimicro USB PC Camera (ZS0211).

hope this helps.
Art2U

---

