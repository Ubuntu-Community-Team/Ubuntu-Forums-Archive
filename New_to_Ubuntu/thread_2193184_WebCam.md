---
title: "WebCam"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by Glkanter on 2013-12-11
Hi,

I tried to be prepared before I went to the store, so I printed out this web page: [http://www.ideasonboard.org/uvc](http://www.ideasonboard.org/uvc) and took it with me.

I found the Creative Live! Cam Sync HD at the store for $25. The box says it is compatible with Linux Kernel 2.6.

I plug it in to a USB port, the green light on the cam lights for a moment, then it goes out.

I can't find any indication that the camera and microphone are present. Skype doesn't seem to know it's connected. Ubuntu system preferences and the like don't seem to know it's connected.

Can anybody help?

Thanks!

Garry

---

### Post by mikewhatever on 2013-12-11
I can't find "Creative Live! Cam Sync HD" in that list. Would you open a terminal window, type in **lsusb**, and post the output.

---

### Post by Glkanter on 2013-12-11
Thank you for the prompt reply.

I found *this* webcam on the list, though: 041e:406c 	  Creative Live! Cam Sync[TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
Here is the results of the **lsusb:**

garry@garry-s5-1204:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04ca:004b Lite-On Technology Corp. 
Bus 001 Device 004: ID 03f0:6b11 Hewlett-Packard Photosmart C4500 series
Bus 001 Device 005: ID 03f0:3a17 Hewlett-Packard Printing Support
Bus 002 Device 003: ID 0a05:7220  
Bus 002 Device 019: ID 041e:4095 Creative Technology, Ltd 
Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 017: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 006: ID 13fe:3e00 Kingston Technology Company Inc. 
Bus 002 Device 007: ID 154b:005b PNY 
garry@garry-s5-1204:~$ 

Thanks so much!!

Garry

---

### Post by jan-goebel-g on 2013-12-11
Try to install cheese > 
[LIST=1]
[*=left]sudo apt-get install cheese
[/LIST]

It should be working already, [this site](https://wiki.ubuntu.com/SkypeWebCams) says so.

---

### Post by Glkanter on 2013-12-11
I will install cheese.

However, the link you provided says this:
 "Remember that Skype cannot access a camera video stream if another  program (like Cheese or guvcview) is already viewing it. Close any such  program and re-select the Skype video settings preview image before  concluding that it doesn't work."

And Skype is why I'm doing all this in the first place.

Thanks!

---

### Post by Glkanter on 2013-12-11
I have successfully installed cheese, and now have a functioning Webcam.

Skype is acting as I was hoping, but I have not yet done an actual test call.

Thanks so much!

---

### Post by Glkanter on 2013-12-11
Skype and the webcam camera are working, but the microphone is not.

Please see the attached status.

I opened the only microphone configuration tool I could find, which is Sound Recorder.

Thanks!


[IMG]http://img35.imageshack.us/img35/8453/5gke.png[/IMG]

---

### Post by asus-user on 2013-12-11
> **Glkanter said:**
>  "Close any such  program and re-select the Skype video settings preview image before  concluding that it doesn't work."
And Skype is why I'm doing all this in the first place.


:)
~
now I can get that cam too without worrying! OR not..

---

### Post by mikewhatever on 2013-12-12
Glkanter, you should be able to select the USB mic device in the Ubuntu sound settings. That is accessed by clicking the speaker icon in the default installation. Note that Skype and Sound Recorder are not the right tools for that.

---

### Post by Glkanter on 2013-12-12
Thanks for that instruction.

Sometimes I'm my own worst enemy when it comes to troubleshooting. I had given up on system settings when I couldn't find anything about webcam video there.

Once I clicked on the correct microphone input option, problem solved.

This is the best support forum I've ever been a part of. Happy holidays to all!!

---

