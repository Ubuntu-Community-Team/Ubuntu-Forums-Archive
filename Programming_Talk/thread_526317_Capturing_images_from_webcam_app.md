---
title: "Capturing images from webcam app"
date: 2007-08-15
forum: Programming Talk
---

### Post by abuntu-handicapped on 2007-08-15
How can i access my webcam and have it automatically save the images to harddrive?

Is there a C++ program that anybody knows of that when run can do this? I would need to get into the code.

---

### Post by Warren Watts on 2007-08-15
There is an application called Motion that will do what you are looking for.

From  Synaptic:> V4L capture program supporting motion detection
Motion is a program that monitors the video signal from
one or more cameras and is able to detect if a significant
part of the picture has changed. Or in other words, it can
detect motion.

Motion is a command line based tool. It has no graphical
user interface. Everything is setup either via the
command line or via configuration files.

The output from motion can be:
   - jpg files
   - ppm format files
   - mpeg video sequences

Also, motion has its own minimalistic web server. Thus,
you can access the webcam output from motion via a browser.

I believe that Motv will also do what you need

Both apps are in the Ubuntu Repositories

---

### Post by abuntu-handicapped on 2007-08-15
Thank you for your reply.

it says that cannot open dev/video0 (both motion and motv). I have been getting the same error in camorama and could actually only get the webcam working in ekiga. It is a logitech pro 5000 and according to most forums people really have trouble with this. 

Any suggestions what to do?

Perhaps buy another webcam that installs easily and runs on /dev/video0?

Not sure if this is relevant but it also says no file or directory (meaning the /dev/video0)

---

### Post by buntunub on 2007-08-15
Based on your question I should think you are looking for a much simpler solution that Motion or Motv. Simply use Ekiga (comes with default Ubuntu install) to take snapshots, or use luvcview to save video streams to hard drive. Motion is a program designed for Security purposes and not for the average user that just wants to capture video.

---

### Post by s1ightcrazed on 2007-08-15
I would also suggest: [ffmpeg]("http://ffmpeg.mplayerhq.hu/"). ffmpeg can read V4l output and can encode that output to whatever format you want (jpg, mpeg, avi, flash video etc...etc..). 

ffserver is a branch project that can serve up streamed content (for instance, multi-part JPEG that has been captured from your webcam) on the web over http.

---

### Post by abuntu-handicapped on 2007-08-15
thanks for your reply buntunub,

see, the problem is, is that its a bit more complicated than simply working a webcam. Okay, im going to try explain what im trying to do without boring you and the rest of the guys i am asking help from...

Bare with me...

I need to run a program (or C++ code or similar) that when run, will capture images from my webcam and download it to hard disk. I need the code for that program that is going to do this as well, so that, the person that takes over from me in this project can manipulate that code or add onto it, depending what they want to do, whether it be auto contrasting or what ever. Once i have that code however, before sending it to the next poor soul, i have to somehow create some sort of motion estimation that might eliminate vibration.

So...thats pretty much the jist of where im trying to get, but seem to be going nowhere slowly.

I hope you guys dont get scared off now, but perhaps its better if you guys know where im trying to get to.

Any thoughts?

---

### Post by abuntu-handicapped on 2007-08-15
S1ightcrazed,

Thanks for the suggestion. I have downloaded it and run it, but have not got it up yet. It also says that it failed to open video device /dev/video0: No such file or directory.

Just a quick comment. I see that it has an option to run it using motion compensation so if i could get this working it might be just what im looking for!!

---

### Post by abuntu-handicapped on 2007-08-15
I was looking at the wrong line with respects to cant open /dev/video0.

This is what it says when i ffmpeg - but nothing happens except what it says below and then about 100 options below it.

[B]neil@neil-desktop:~$ ffmpeg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
usage: ffmpeg [[infile options] -i infile]... {[outfile options] outfile}...
Hyper fast Audio and Video encoder

Main options:[/B]

Appreciate all responses.

---

### Post by abuntu-handicapped on 2007-08-15
Does anyone know if i will be able to get into the code of ffmpeg if i do actually get it capturing frames from my webcam?

---

### Post by s1ightcrazed on 2007-08-15
Typically with ffmpeg you would do something like:

ffmpeg -i /dev/file image.jpg

-i is for input. So you need to know where the input is coming from. Is it a USB device, a V4l (video4linux) device; what is the device file? Once we have that we just tell ffmpeg to grab that, and encode it into a jpg called image.jpg. 

Check out the [ffmpeg documentation]("http://ffmpeg.mplayerhq.hu/documentation.html") and the [faq]("http://ffmpeg.mplayerhq.hu/faq.html").

---

### Post by abuntu-handicapped on 2007-08-16
Slightcrazed,

It is a usb webcam, but i am not sure where the input is coming from. Does this help?

neil@neil-desktop:~$ lsusb
Bus 001 Device 007: ID 046d:08ce Logitech, Inc. 
Bus 001 Device 005: ID 1307:0163  
Bus 001 Device 001: ID 0000:0000  
neil@neil-desktop:~$

---

### Post by obscur156 on 2008-03-18
wxcam...
[http://wxcam.sourceforge.net/]("http://wxcam.sourceforge.net/")

---

