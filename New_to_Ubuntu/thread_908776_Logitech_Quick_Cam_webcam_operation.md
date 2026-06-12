---
title: "Logitech Quick Cam webcam operation"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by richg on 2008-09-02
Hi All

I just received a Logitech Quick Cam Communicate Deluxe webcam and it works with my Xandros EEE 4G PC. 
It shows up as v412 UVC Camera (046d:0992) under Device.
I use the default Video Format, (only one format) and 640 X 480.
I am using the 4G PC default application for the web cam ucview.real 0.14 a video capture application.
[http://www.unicap.org](http://www.unicap.org)

One page I found showed Ubuntu 7.10 with this webcam. This webcam was not listed under 8.04.
I think I saw a message about downloading a file for use with 8.04. Cannot remember where.
Right now I just want real time video capture. If I can ever get a IM application  with video & audio, I will see if I can get it to work there also.
Thanks in advance.

Rich

---

### Post by Crafty Kisses on 2008-09-03
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by richg on 2008-09-03
Ok, thanks for the reply. I used synaptic package manager to download Ekiga but the setup did not seem to have much of anything to do with webcams. I was supposed to set up some kind of account and select dial up or cable. I have cable. This did not seem to make sense so I aborted the setup. There was more than one Ekiga in the synaptic. Maybe I got the wrong one.

Here is the result of lsusb 

lexon@lexon-desktop:~$ lsusb 
Bus 005 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard 
Bus 005 Device 003: ID 0409:005a NEC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20 
Bus 001 Device 007: ID 046d:0992 Logitech, Inc. 
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub 
Bus 001 Device 001: ID 0000:0000  

This is the webcam, Bus 001 Device 007: ID 046d:0992 Logitech, Inc. 

Rich

I guess I did something wrong. I clicked the thank you icon but it did not show up.
I hope Ubuntu will make that option more intuitively obvious. I am not the only one who has missed it.

---

### Post by richg on 2008-09-03
I decided to continue the setup for Ekiga and I saw I did not have to subscribe to anything. The camera does work but this application is only for a Instant Messenger application.

I would like an application that will allow me to record and save the video to my PC.

My EEE 4G PC allows me to do that but that PC has only 4gb total flash drive for OS and Files.
Thanks.

Rich

Ok, I managed to get Cheese to work. Thanks all for the help.

---

### Post by no2498 on 2009-09-05
wxcam is better

---

### Post by executorvs on 2009-09-09
what is wxcam, I'm not seeing it in synaptic

---

### Post by cariboo on 2009-09-09
Try cheese, it is in the repositories.

---

### Post by executorvs on 2009-09-09
I'm familiar with cheese and camorama but neither were as robust in any way as what I'm looking for.
this is the thread I started earlier explaining what I'm looking for [http://ubuntuforums.org/showthread.php?p=7940117](http://ubuntuforums.org/showthread.php?p=7940117) .
I didn't realize that I could do a capture through vlc or kdenlive till today though and, assuming I can get them working, will be at least a partial solution to my endevor.

---

### Post by bear24rw on 2009-09-09
check out guvcview, when i was working with some uvc cams i had to disable auto exposure and auto white balance (i think it was white balance it was auto something) to get decent frame rates

---

### Post by no2498 on 2009-09-14
[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)




try that

---

