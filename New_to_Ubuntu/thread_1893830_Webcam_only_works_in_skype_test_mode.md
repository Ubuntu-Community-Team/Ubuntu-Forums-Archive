---
title: "Webcam only works in skype test mode"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by Zvanochek on 2011-12-11
Another Skype vs Linux issue I'm afraid. My apologies if this has come up before, but the previous posts I've read all had slightly different issues.

My first forray into Ubuntu (11.10) yesterday hit a snag in that my webcam (Logitech C200) won't work correctly in Skype (2.0 beta). Neither video or sound works, except when I go into options; in options, the test function turns on my camera, and it works fine, but otherwise, nothing.

Having hit the forums, I tried it on Cheese, and it works fine with that.

:confused:

Any and all suggestions would be greatly received. I'm computer literate, and know some Java etc (so understand the concept of command line), but I am ignorant in terms of Linux.

Zvanochek

Running Ubuntu 11.10 (32 bit)
Webcam C200 - 046d:0802 Logitech, Inc. Webcam C200
Skype v2.2.0.35-0oneiric2

---

### Post by bizi on 2011-12-11
hi dont know if it helps but.....next time when you try skype with camera .....open terminal and type "dmesg | tail" see if there is any error about skype......

make sure you have set skype corectly...enable skype video, recive video from anybody, show i have video to people i have allowed

as far as i remember when you open video chat in skype there is somthing like show information about conversation or connection see what says there 

post results

---

### Post by Zvanochek on 2011-12-11
Still no luck, and no error messages. One thing I have noticed it that although the video is set to receive from my webcam, the microphone is set as Pulse audio server. Is that the issue, and if so, how can I change it.

Another note is that the camera power light only turns on during the test mode, note when Skype starts, which if I recall correctly, it did with XP.

---

### Post by mastablasta on 2011-12-11
try launching skype from terminal with the following command (copy & paste it):

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by Zvanochek on 2011-12-11
When I try that, skype loads, but the following error message appears (and still no camera function). Is it perhaps a driver issue, despite working in Cheese?


ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by Rinre on 2011-12-11
I can't pretend that I understand the above help, but whe Skype was being troublesome on my computer (both sound and audio malfunctioning) I tried another skype version for tablets/mobile devices and it worked like a charm :)

Maybe not the most genious solution, but might be worth a try, at least if nothing else works

---

### Post by Zvanochek on 2011-12-12
I have read in a Ubuntu wiki that Skype 2.1.4 works well with my webcam, but I couldn't find a copy anywhere. Thanks for the suggestion, I might use that as a last resort.

---

### Post by mastablasta on 2011-12-12
> **Zvanochek said:**
> When I try that, skype loads, but the following error message appears (and still no camera function). Is it perhaps a driver issue, despite working in Cheese?
 
 
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
 
(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
(skype:2417): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
strange.
 
no it's not driver's issue. If it works in cheese. it's a skype issue. 
 
Try to uninstall skype and download the .deb from their skype for linux website and install that one.
 
 
you can also open terminal
 
input: gstreamer-properties
 
then you can test and see what is set as default video driver.
 
 
as i know Logitech cameras should work out of the box as they have drivers for linux.

---

### Post by Zvanochek on 2011-12-12
Thanks for the suggestion, I'll give it a try tonight and get back to you.

---

### Post by donkyhotay on 2011-12-12
I've never used skype with a webcam so I could be wrong on this but at one point I remember hearing that skype changed their protocols a few years ago and because of this video chat no longer works between linux and windows/osX anymore. I don't even own a webcam so I've never really tried but I do know I have never seen a video chat from my friends who use windows systems even though they see each other.

---

### Post by jockyburns on 2011-12-12
When you start skype. right click the skype icon (top right of your computer screen) and select options from the drop down menu. Then select "Video devices" and check that it's set to usb camera. 
I had a similar problem, in as much as skype was trying to use my TV tuner card as a video device.

---

### Post by Zvanochek on 2011-12-12
> **jockyburns said:**
> When you start skype. right click the skype icon (top right of your computer screen) and select options from the drop down menu. Then select "Video devices" and check that it's set to usb camera. 
I had a similar problem, in as much as skype was trying to use my TV tuner card as a video device.
 
The camera is selected, as when I click test on the video devices tab, it turns on and works.

---

### Post by Zvanochek on 2011-12-12
> **mastablasta said:**
> strange.
 
no it's not driver's issue. If it works in cheese. it's a skype issue. 
 
Try to uninstall skype and download the .deb from their skype for linux website and install that one.
 
 
you can also open terminal
 
input: gstreamer-properties
 
then you can test and see what is set as default video driver.
 
 
as i know Logitech cameras should work out of the box as they have drivers for linux.

I went through Skype to get the .deb file, but they only had Skype for Ubuntu 10.4, where as I am running 11.10. Could this be the problem? Should I roll back to the older Ubuntu?

With regards to the gstreamer-properties, I sent the audio and video input to the correct usb camera option, and the drivers to Pulse, but still no luck. Skype just doesn't seem to connect to the camera except when it is running the test mode.

---

### Post by mastablasta on 2011-12-13
> **donkyhotay said:**
> I've never used skype with a webcam so I could be wrong on this but at one point I remember hearing that skype changed their protocols a few years ago and because of this video chat no longer works between linux and windows/osX anymore. I don't even own a webcam so I've never really tried but I do know I have never seen a video chat from my friends who use windows systems even though they see each other.
 
 
it works ok with windows OS. been using it before i got a cam on XP maschine.

---

### Post by mastablasta on 2011-12-13
> **Zvanochek said:**
> I went through Skype to get the .deb file, but they only had Skype for Ubuntu 10.4, where as I am running 11.10. Could this be the problem? Should I roll back to the older Ubuntu?

you could try to install it. before i used 9.10 deb version on 10.10. later they had some updates so i used this 10.04 deb version on 10.10. 
 
> 
With regards to the gstreamer-properties, I sent the audio and video input to the correct usb camera option, and the drivers to Pulse, but still no luck. Skype just doesn't seem to connect to the camera except when it is running the test mode.
 
 
That's really strange. why would it work in test but not in video... try running skype from terminal to see if there are any errors. I would also suggest you try official Skype (for linux) forums. [http://community.skype.com/t5/Linux/bd-p/Linux](http://community.skype.com/t5/Linux/bd-p/Linux)
 
it might take a while to get an answer but usually there is a reply. I am still thinking it is something with that preload command.
 
here is some more data for V4L2 drivers: [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

---

### Post by Zvanochek on 2011-12-13
> **mastablasta said:**
> you could try to install it. before i used 9.10 deb version on 10.10. later they had some updates so i used this 10.04 deb version on 10.10. 
 
 
 
 
That's really strange. why would it work in test but not in video... try running skype from terminal to see if there are any errors.

 
Tried that, but nothing came up
 
> **mastablasta said:**
>  I would also suggest you try official Skype (for linux) forums. [http://community.skype.com/t5/Linux/bd-p/Linux](http://community.skype.com/t5/Linux/bd-p/Linux)
 
it might take a while to get an answer but usually there is a reply. I am still thinking it is something with that preload command.
 

 
I'll give them a buzz and see what they say. Thanks for your help. If I find an answer, I'll pop it back here.

---

### Post by Zvanochek on 2011-12-14
> **Zvanochek said:**
>  
I'll give them a buzz and see what they say. Thanks for your help. If I find an answer, I'll pop it back here.
 
No-one has suggested a solution on the skype forum; Is there another forum you guys could suggest I ask?

---

### Post by Ms. Daisy on 2011-12-14
I had some difficulty setting up my logitech webcam when I installed skype on Ubuntu.  It took some configuring but I can't remember what I did.  I was able to fix it through the GUI. I think I had to mess around with the settings for the camera (outside of Skype). When I get back to that computer later today, I'll see if I can dig up what I did.

---

### Post by Ms. Daisy on 2011-12-14
> **donkyhotay said:**
> I've never used skype with a webcam so I could be wrong on this but at one point I remember hearing that skype changed their protocols a few years ago and because of this video chat no longer works between linux and windows/osX anymore.
Recently I've video skyped from an Ubuntu machine to another windows machine, so that wasn't true for me.  I'm still looking for my info.  But meanwhile, do you have a firewall or apparmor configured?  Could be conflicting.

---

### Post by Zvanochek on 2011-12-15
> **Ms. Daisy said:**
> Recently I've video skyped from an Ubuntu machine to another windows machine, so that wasn't true for me. I'm still looking for my info. But meanwhile, do you have a firewall or apparmor configured? Could be conflicting.
 
Do you know the command for the checking the config of the firewall/apparmor?

---

### Post by Zvanochek on 2011-12-15
Ah, do you mean the ufw?

---

### Post by Ms. Daisy on 2011-12-15
Well, you have to install apparmor, so if you don't know if you've got it then you probably don't. 
Uncomplicated firewall is installed by default in 11.10, but all ports are open unless you configured it.  So again, if you don't know then it's probably not the problem.

OK, finally figured out what I did to make the logitech webcam work in skype. The problem is that Skype doesn't choose the webcam by default. And if there is no built-in video or mic, then nothing is enabled.  When you've got Skype open, go to sound preferences.  (not entirely sure how to get there in 11.10- I've got an applet for sound on the menu bar, hopefully you do too.)  
Under the "hardware" tab you should see your webcam (mine is called "analog mono input" for some reason, I guess "logitech" would have been too easy). Make sure the profile is set to "analog mono input".  
On the "input" tab make sure that you've selected the webcam radio button (again the webcam is called "analog mono"). Say something and you should see it's accepting sound input.  Once you have that configured, then the video in skype works as well. 

I tested it on the echo/sound test service and for some reason video won't work.  But when I actually called a friend, my video & sound worked perfectly.  

Post back if this doesn't fix it.

---

### Post by Zvanochek on 2011-12-15
> **Ms. Daisy said:**
>  
OK, finally figured out what I did to make the logitech webcam work in skype. The problem is that Skype doesn't choose the webcam by default. And if there is no built-in video or mic, then nothing is enabled. When you've got Skype open, go to sound preferences. (not entirely sure how to get there in 11.10- I've got an applet for sound on the menu bar, hopefully you do too.) 
Under the "hardware" tab you should see your webcam (mine is called "analog mono input" for some reason, I guess "logitech" would have been too easy). Make sure the profile is set to "analog mono input". 
On the "input" tab make sure that you've selected the webcam radio button (again the webcam is called "analog mono"). Say something and you should see it's accepting sound input. Once you have that configured, then the video in skype works as well. 
 
I tested it on the echo/sound test service and for some reason video won't work. But when I actually called a friend, my video & sound worked perfectly. 
 
Post back if this doesn't fix it.
 
Just to clarify, do you mean sound preferences in Ubuntu or in Skype? Thanks for the suggestion.

---

### Post by Ms. Daisy on 2011-12-15
I haven't found a way to get to the sound preferences through skype itself.  So I used sound preferences while skype is open and running.

---

### Post by Zvanochek on 2011-12-15
> **Ms. Daisy said:**
> Well, you have to install apparmor, so if you don't know if you've got it then you probably don't. 
Uncomplicated firewall is installed by default in 11.10, but all ports are open unless you configured it.  So again, if you don't know then it's probably not the problem.

OK, finally figured out what I did to make the logitech webcam work in skype. The problem is that Skype doesn't choose the webcam by default. And if there is no built-in video or mic, then nothing is enabled.  When you've got Skype open, go to sound preferences.  (not entirely sure how to get there in 11.10- I've got an applet for sound on the menu bar, hopefully you do too.)  
Under the "hardware" tab you should see your webcam (mine is called "analog mono input" for some reason, I guess "logitech" would have been too easy). Make sure the profile is set to "analog mono input".  
On the "input" tab make sure that you've selected the webcam radio button (again the webcam is called "analog mono"). Say something and you should see it's accepting sound input.  Once you have that configured, then the video in skype works as well. 

I tested it on the echo/sound test service and for some reason video won't work.  But when I actually called a friend, my video & sound worked perfectly.  

Post back if this doesn't fix it.

Works perfectly. Thank you so much! I'll label this as a fixed issue. Thanks again.

Zvanochek

---

