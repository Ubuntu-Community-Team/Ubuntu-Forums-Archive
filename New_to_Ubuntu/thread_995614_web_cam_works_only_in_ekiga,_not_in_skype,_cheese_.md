---
title: "web cam works only in ekiga, not in skype, cheese or camorama"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by ujjwalkumar on 2008-11-28
I have been trying very hard to setup my webcam for skype. I am on Hardy Heron. My webcam specification is: ZC0301P .. dmesg shows: 
```

[ 1690.282469] usb 2-3.4: new full speed USB device using ohci_hcd and address 6
[ 1690.335556] usb 2-3.4: configuration #1 chosen from 1 choice
[ 1690.336625] usb 2-3.4: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8:0x303B)
[ 1690.384377] usb 2-3.4: PB-0330 image sensor detected
[ 1690.669098] usb 2-3.4: Initialization succeeded
[ 1690.669156] usb 2-3.4: V4L2 device registered as /dev/video0
```

The webcam works fine with ekiga with v4l2 settings, and not with v4l settings. It doesn't work with kopete, skype, cheese or camorama. I have visited most of the threads concerning this topic, but had no luck with that.

gstreamer-properties shows on testing with v4l2 :
```

'Video for Linux 2 (v4l2): Could not negotiate format"
```

the whole error message in console is: 

```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2387): gst_base_src_start (): /pipeline1/v4l2src3:
Check your filtered caps, if any]
```


camorama shows: ```
Could not connect to video device (/dev/video0). Please check connection.
```

Is there any other way to use video chat in skype (any other parameters or v4l2 settings)??

Please help me with that. I have spent 2 sleepless nights to configure video chat with skype, but was unsuccessful.

I can see the camera in skype. but when I click on test, the area becomes green.

---

### Post by whitehathacker on 2008-11-28
I just moved to ubuntu from vista.. I know my camera works because i used cheese to test it out.. but on my skype options i do not see the camera option i gues skype doesnt see the camera.. any help?? thanks!!

---

### Post by ujjwalkumar on 2008-11-28
> **whitehathacker said:**
> I just moved to ubuntu from vista.. I know my camera works because i used cheese to test it out.. but on my skype options i do not see the camera option i gues skype doesnt see the camera.. any help?? thanks!!

but, in my case, the cam doesn't even work with cheese. it only works with ekiga, with v4l2 settings.. also, I can see the camera option in skype.. when I click on test, the area becomes green.. :(

---

### Post by ujjwalkumar on 2008-11-30
no response!!

---

### Post by dineshs on 2008-11-30
Did you try installing easycam2 ? .Ithink it will install the correct driver for your webcam.I am not sure

---

### Post by ujjwalkumar on 2008-11-30
> **dineshs said:**
> Did you try installing easycam2 ? .Ithink it will install the correct driver for your webcam.I am not sure

easycam2 gave me a french error message: 
```

Ce driver n'est pas compatible avec Easycam, ou l'orthographe est incorrecte ... ou il n'existe pas :)

```

which in english means:
```

This driver is not compatible with EASYCAM or spelling is wrong ... or no:)

```

please help!!

---

### Post by ujjwalkumar on 2008-12-02
finally, after a lot of struggle, I figured out one thing:
the webcam works, if before shutdown, it was unplugged, and replugged **after** the computer boots completely (for this, easycam2 should be installed). but, if the webcam was initially plugged in before the computer was booting, the webcam doesn't work..

so, the problem lied in the loading of modules..

the clue is to either unplug webcam everytime before shutting down the computer or trying this (which worked for me very well):

1. install easycam2 : [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

2. install the webcam driver by going to applications>accessories>easycam2 (the camera should be plugged in before install)

3. now, unload the zc0301 and gspca modules by typing this in the console:
```

sudo modprobe -r zc0301
sudo modprobe -r gspca

```
here zc0301 can be replaced with your webcam chipset. to know it, check 
```

lsmod | grep gspca

```
and you can find suitable module (like zc0301)
4. load the gspca module again by typing:
```

sudo modprobe gspca

```

5. you will now see that the webcam has started working.. if cheese was loaded, it would have started automatically to take pictures.. :)

This procedure worked for me.. Please reply if it worked for you too :)

---

### Post by noukist on 2009-03-25
> **ujjwalkumar said:**
> finally, after a lot of struggle, I figured out one thing:
the webcam works, if before shutdown, it was unplugged, and replugged **after** the computer boots completely (for this, easycam2 should be installed). but, if the webcam was initially plugged in before the computer was booting, the webcam doesn't work..

so, the problem lied in the loading of modules..

the clue is to either unplug webcam everytime before shutting down the computer or trying this (which worked for me very well):

1. install easycam2 : [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

2. install the webcam driver by going to applications>accessories>easycam2 (the camera should be plugged in before install)

3. now, unload the zc0301 and gspca modules by typing this in the console:
```

sudo modprobe -r zc0301
sudo modprobe -r gspca

```
here zc0301 can be replaced with your webcam chipset. to know it, check 
```

lsmod | grep gspca

```
and you can find suitable module (like zc0301)
4. load the gspca module again by typing:
```

sudo modprobe gspca

```

5. you will now see that the webcam has started working.. if cheese was loaded, it would have started automatically to take pictures.. :)

This procedure worked for me.. Please reply if it worked for you too :)

ok first i have to thank you but that doesn't appear to work in my computer. Maybe i did something wrong but i 've done everything that you tell us to do and i can't find anywhere my web cam :S 

any idea ?

thanks in advance

EDIT*** :

wrong alert done :) 
thank u a lot !! the only problem i have is that it can't find the microfone, that's no big problem because i had bought one microsoft microfone and i go to the skype setting choose that as microfone and it's ok but it has a low sound :S 

if you have any idea for that pm me please :)


thanks again !

---

### Post by starcannon on 2009-03-25
I've had great luck with the berliOS UVC driver/module in the past; though, the latest berliOS module/driver does require one to compile them from source. 

You can find the download link here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

And a wiki with a guide here: [http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)

The guide was written for Ubuntu 6.06 but still works fine in Ubuntu 8.04 and 8.10.

I have also found that for my laptop needs that 8.10 has "just worked" for the webcam and wifi internals that I have come across so far.

GL
starcannon

---

