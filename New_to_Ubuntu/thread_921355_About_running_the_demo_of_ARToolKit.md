---
title: "About running the demo of ARToolKit"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by smallcamel on 2008-09-16
I want to use ARToolKit in Ubuntu and I have successfully compiled the ARToolKit.
But when I tried to run the simpleTest, the problem occurred,
and the error code can be posted as the following:

msp@msp:~/Desktop/ARToolKit$ cd bin
msp@msp:~/Desktop/ARToolKit/bin$ ./simpleTest
No video config string supplied, using defaults.
error: setting configuration !! bad palette mode..
TIPS:try other palette mode (or with new failure contact ARToolKit Developer)

I googled for a long time but still haven't found any solution..
My camera is Logitech QuickCam Pro 3000 and when I run the ./Configure, my option is 1, n, y, y.

So anyone who knows the solution please help me.
Thank you very much.

---

### Post by prabhash1985 on 2009-01-14
Hi,

I'm also having the same problem. I posted a message today to the artoolkit's official web site as well.

I think there is something to do with the vconf in examples/simpleTest.c and the other files as well. I am using A4Tech webcam. It worked fine with artoolkit in windows platform, but not in ubuntu. I use the web cam very well for opencv. So, it's not a problem with ubuntu such that the webcam is not recognized. I think we have to set some parameter.

Let's see what reply is and I will post it here.

Prabhash

---

### Post by skullmunky on 2009-01-21
I don't know if it'll solve your problem, but here's what I did.

1. I have a MacBook Pro (1,1), using the built-in iSight camera.
2. Installed the drivers for that following the normal wiki instructions
3. Verified it works with Cheese

I first tried compiling ARToolkit with V4L support, but it gave those kinds of errors.

Then tried compiling with GStreamer support, since GStreamer is what Cheese uses, and I know that works.  Got different errors, solved by editing the example code config lines like so:

4. Open simpleTest.c
5. the line ```
 char *vconf="";
``` is the culprit.  It's the configuration for GStreamer.  One would hope that if it's blank, GStreamer would pick a nice sensible default.  Alas.

6. change it to:
```

char *vconf = "v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24,width=320,height=240 ! identity name=artoolkit ! fakesink";

```
BLEAH!  what's all that?  In brief: GStreamer works by chaining together modules. One module is piped to the next with the !.  

1. ```
v4l2src device=/dev/video0 use-fixed-fps=false
```
Using Video4Linux2, set the device to /dev/video0, etc.  There are probably more options, who knows what they are.
2. ```
ffmpegcolorspace
``` converts the color space of the video stream, e.g. from YUV to RGB
3. ```
capsfilter caps=video/x-raw-rgb,bpp=24,width=320,height=240
```
set the capture parameters; 24 bit, 320x240, and some other stuff.
4. ```
 identity name=artoolkit 
``` I guess you use this to refer to the stream later?
5. ```
fakesink
``` a 'sink' is something that does something with the data stream, such as displaying it, writing to disk, network, etc.  fakesink is just a generic terminator to hold the data so ARToolkit can manipulate it.   I think.

---

### Post by pomalin on 2009-07-12
Hello, this is what I have when I try to run simpleTest from artoolkit.

```
Using supplied video config string [v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24,width=320,height=240 ! identity name=artoolkit ! fakesink].
ARVideo may be configured using one or more of the following options,
separated by a space:

DEVICE CONTROLS:
 -dev=filepath
    specifies device file.
 -channel=N
    specifies source channel.
 -noadjust
    prevent adjusting the width/height/channel if not suitable.
 -width=N
    specifies expected width of image.
 -height=N
    specifies expected height of image.
 -palette=[RGB|YUV420P]
    specifies the camera palette (WARNING:all are not supported on each camera !!).
IMAGE CONTROLS (WARNING: every options are not supported by all camera !!):
 -brightness=N
    specifies brightness. (0.0 <-> 1.0)
 -contrast=N
    specifies contrast. (0.0 <-> 1.0)
 -saturation=N
    specifies saturation (color). (0.0 <-> 1.0) (for color camera only)
 -hue=N
    specifies hue. (0.0 <-> 1.0) (for color camera only)
 -whiteness=N
    specifies whiteness. (0.0 <-> 1.0) (REMARK: gamma for some drivers, otherwise for greyscale camera only)
 -color=N
    specifies saturation (color). (0.0 <-> 1.0) (REMARK: obsolete !! use saturation control)

OPTION CONTROLS:
 -mode=[PAL|NTSC|SECAM]
    specifies TV signal mode (for tv/capture card).

```

How to get it to work please ? Or is there another solution for Augmented Reality with linux ?

---

### Post by Mecasickle on 2010-02-22
Wow! It's been a year since the last post on this thread :D ...

But I'm encountering the same problem as well. What should I do!?!?!?!

---

### Post by realidadeaumentada on 2010-06-15
I have the final Ubuntu version 10.04, and i install ARTollkit, and i can compile the files but when i try run simple test or other example, give me the follow error:

No video config string supplied, using defaults.
error: setting configuration !! bad palette mode..
 TIPS:try other palette mode (or with new failure contact ARToolKit Developer)

who can help????

---

### Post by zenuz on 2010-09-06
After some research, I found that this settings work for me in Ubuntu 10 in a macbook (2-1).

char *vconf = "v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink ! identity name=artoolkit";

Hope it helps somebody.
Cheers

---

### Post by zenuz on 2010-09-06
Just a small correction and quick note.
I finally managed to compile ARToolkits in ecplise, debug mode.
So just some footnotes that might help others facing problems just as I did:
- The ' char * vconf = ""; ' should be changed to:
char *vconf = "v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb ! identity name=artoolkit ! fakesink";
(actually 'capsfilter caps=' can be ignored. ximagesink did not work, and I preffer setting the width and height manually.)
- If you are not sure which '/dev/video?' is, just check cheese.
- The path should all be absolute (at least I had troubles with relative paths.)
- Install the latest version of glut( actually I installed "mesa" demos' directly from the source. The synaptic version was outdated and I finally solved my problems with glut in the function "argDispImage( dataPtr, 0,0 );"  after I installed mesa. but that might be just casual... )
And good luck for you, I hope you don't spend half the time I did trying to set this up.
P.S. on MacOSX I just had to download and compile it :p

---

### Post by skr13 on 2010-10-12
Hi,

I have successfully configured and built the ARToolkit 2.72 on my Ubuntu(Karmic) for gstreamer(I have a USB camera). But I am unable to run the simpleTest. I get segmentation fault when I run it.

The ARTOOLKIT_CONFIG variable is set as:
[FONT="Courier New"]
ARTOOLKIT_CONFIG="v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24 ! identity name=artoolkit ! fakesink sync=0"[/FONT]

I can launch the gstreamer with the command:

[FONT="Courier New"]#gst-launch v4l2src ! xvimagesink[/FONT]

I get the video output from the webcam.

But when I run the simpleTest, I get a segmentation fault. The output is:


[FONT="Courier New"]$ ./simpleTest
Using config string from environment [v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24 ! identity name=artoolkit ! fakesink sync=0].
libARvideo: GStreamer 0.10.25
libARvideo: GStreamer pipeline is PAUSED!
libARvideo: GStreamer negotiated 640x480
libARvideo: GStreamer pipeline is PLAYING!
libARvideo: GStreamer pipeline is PAUSED!
Image size (x,y) = (640,480)
*** Camera Parameter ***
--------------------------------------
SIZE = 640, 480
Distortion factor = 318.500000 263.500000 26.200000 1.012757
700.95147 0.00000 316.50000 0.00000 
0.00000 726.09418 241.50000 0.00000 
0.00000 0.00000 1.00000 0.00000 
--------------------------------------
Segmentation fault
[/FONT]

Also a window pops up and closes. I am new to AR.

Any idea where I am going wrong.

Thanks

---

### Post by christianh on 2011-01-19
Hi,

I compiled the ARToolkit 2.71.1 from the tar ball on a 32bit lucid installation. At first I had the same results as skr13, but in the end it came down to finding the right gstreamer settings. It seems like figuring out the right scaling or rescaling settings are crucial depending on your camera model.

In the successful test I used a Creative camera that is identified by lsusb as

[FONT=Courier New]041e:4061 Creative Technology, Ltd Live! Cam Notebook Pro [VF0400][/FONT]

With that, simpleTest ran fine with the command

[FONT=Courier New]$ ARTOOLKIT_CONFIG="v4l2src device=/dev/video0 ! video/x-raw-yuv,width=640,height=480 ! videoscale ! video/x-raw-yuv,width=480,height=320 ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24 ! identity name=artoolkit ! fakesink" ./simpleTest[/FONT]

The report on [http://www.poweroftwo.de/index.php/2008/11/04/artoolkit-kamera-kalibration](http://www.poweroftwo.de/index.php/2008/11/04/artoolkit-kamera-kalibration) helped a lot finding the right settings (text is in German).

Hope that helps. I can post some more about my way of getting the ARToolkit compiled on the 32bit lucid in case anyone is interested...

---

### Post by skr13 on 2011-02-01
Hi,

The configuration settings that I posted/used worked for me. I had to modify in the simpleTest program. 

I added  argDrawMode2D() before calling the argDispImage()
configuration string:  *vconf ="v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-                          rgb,width=640,height=480 ! identity name=artoolkit ! fakesink sync=0 "

It's been sometime that I worked on it, so I don't exactly remember why I added it but will post about it soon :)

Thanks
skr

---

### Post by mayko on 2011-03-15
Hi, I have the same problem as pomalin. It seems to me that changing of *vconf has no effect at all. I used a few versions of that I found in this thread but still having just that option list. I have tested simpletest and videotest but result is still the same.

So how to get it work? Thanks.

---

### Post by futuraX on 2012-02-06
Greetings,

I am in the same situation. Could anyone guide me to a beginners thread, on how to install or compile the Artoolkit on Ubuntu 11.10. I have recently join the community  of Ubuntu users and I am completely new to this OS. As I understand that most of this installation is done on the console - which I don't have the language or skills for this yet. Which, I would need a step by step assistance to guide me in this process. 
I have so far have downloaded this file from the Artoolkit website: (openvrml-0.16.3-bin-macosx.zip) -which I'm not sure if I have the correct artoolkit file to run on my Ubuntu 11.10 32bit system.

Any suggestions and feed back woud be greatly appreciated. 
Thank you. :) :)

FuturaX

---

### Post by futuraX on 2012-02-08
Greetings,

I have recently followed the prompts or codes on the following thread: [http://ubuntuforums.org/showthread.php?t=343529](http://ubuntuforums.org/showthread.php?t=343529) 

In order to install the ARtoolkit file in the beginning of that thread onto my Ubuntu 11.10 32bit machine - with no success. 

However, I did successfully installed the "build-essential" from the repositories. Using the Code:
"sudo apt-get install build-essential"

However, When I proceeded with the following codes: ./Configure > make > sudo make install

I get the following result: 

futura2020@"":~$ ./Configure
bash: ./Configure: No such file or directory
futura2020@"":~$ make
make: *** No targets specified and no makefile found.  Stop.
futura2020@F"":~$ sudo make install
[sudo] password for futura2020: 
make: *** No rule to make target `install'.  Stop.
futura2020@"":~$ 

Any suggestions would be greatly appreciated! :))

---

