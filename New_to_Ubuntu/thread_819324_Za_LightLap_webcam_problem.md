---
title: "Za LightLap webcam problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by gremial on 2008-06-05
I recently bought a Zareason LightLap and am generally very pleased with it - certainly the right purchase for me. I have a problem, however, with the built-in webcam, which doesn't appear to be working properly.

Here's what I've tried:

Testing video with gstreamer-properties gives colour bars and static as default output but
default input gives a "Failed to construct test pipeline for 'Video for Linux 2 (v4l2)'" error. Likewise, Cheese gives the colour bar output, Booting with a LiveCD makes no difference.

Could someone please advise this noob?

Thanks!

---

### Post by balagosa on 2008-06-05
do you know the exact model, maker of your built-in cam?

type in the result of ```
lsusb
```

---

### Post by gremial on 2008-06-05
Thanks. I don't know the make of the webcam, although the Za branded unit is based on the Asus s62ep. Here's what was produced by lsusb:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 174f:5a3d  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by balagosa on 2008-06-05
> **gremial said:**
> Thanks. I don't know the make of the webcam, although the Za branded unit is based on the Asus s62ep. Here's what was produced by lsusb:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 174f:5a3d  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

your buil-in webcam is "Bus 004 Device 002: ID 174f:5a3d"

i will do searches for your webcam driver. you can help me by searching too.

keyword for searching "174f:5a3d"

---------------------------------------------------------------------------------------
i have found a driver (i think it is; update) but it is only supported for windows.

hey gremial, the pain about having high-end laptops is the hardware support. it can take months for your driver to be available for linux. maybe someone has done it already, so just ask around.

---

### Post by canadianwriterman on 2008-06-05
I have a Zareason LightLap, too, and am very happy with it. Whenever I've had any issues, I've sent a quick e-mail to Earl at Zareason. He's very responsive and can probably answer your question. My webcam works, but I've only tried it through Ekiga.

---

### Post by gremial on 2008-06-05
Thanks folks. I too only found Windows drivers, but at least I now know that someone else's LightLap cam works. I've swapped a couple of emails with Za tech, so I'll press them on this matter.

---

### Post by balagosa on 2008-06-05
better talk to more experinced ZaReason laptop users. (before this post, i had no idea there was such a laptop "brand?")

when it works through Ekiga, it will work through Cheese, Gyache(with some minor flashcam installs). these are the softwares that i have tried.

canadianwriterman, how exactly did you install your cam? (make it work). if you dont mind me asking because learning is what i love.

---

### Post by gremial on 2008-06-05
> **balagosa said:**
> canadianwriterman, how exactly did you install your cam? (make it work). if you dont mind me asking because learning is what i love.

I imagine that it 'just works', which is one of Zareason's selling points, except that my webcam doesn't.

I just started Ekiga and it does actually take a successful image through the webcam at startup, but the program freezes when I press any of the cam-related buttons on its toolbar. Cheese just gives me colour bars.

---

### Post by canadianwriterman on 2008-06-05
> **balagosa said:**
> better talk to more experinced ZaReason laptop users. (before this post, i had no idea there was such a laptop "brand?")

when it works through Ekiga, it will work through Cheese, Gyache(with some minor flashcam installs). these are the softwares that i have tried.

canadianwriterman, how exactly did you install your cam? (make it work). if you dont mind me asking because learning is what i love.

I just opened Ekiga and went through the short setup wizard. When it was finished, Ekiga opened and the webcam was working. Of course, in Ekiga, you can't do anything with the webcam except transmit the image to the receiver of your call. When I get home tonight, I'll try Cheese (although I don't recall seeing it in the Hardy application menu).

---

### Post by balagosa on 2008-06-05
hmmm...strange though.

in my experience i had to look for drivers for my webcam. i tried Ekiga during the pre-driver installation and it did not work. I got the driver installed and tested Ekiga, it worked. so I tried Cheese and Gyachi, same working output.

---

### Post by canadianwriterman on 2008-06-06
Last night, I downloaded Cheese, opened it up on my Zareason LightLap, and the camera "just worked." I would say keep working with the Zareason folks on a solution.

---

### Post by sensouci on 2008-06-06
Hi all,

I also have a ZaReason lightlap and have trouble getting my webcam to work. Balagosa you said having installed a driver to get it to work. Which driver is it please?
Thks

---

### Post by gremial on 2008-06-07
No Linux driver to be found, I'm afraid, but I'll post here whatever Za Tech comes up with.

---

### Post by loell on 2008-06-07
not sure if this helps, but it seems its a syntek webcam?

anyway, try to compile and install this driver,

[http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html]("http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html")

---

### Post by gremial on 2008-06-07
Webcam 174f:5a3d isn't one of the models listed though. Still worth trying?

---

### Post by sensouci on 2008-06-08
Sorry, I have try the stk driver it compiled ok but it did get the webcam to work. (may be I did something wrong)

---

### Post by sensouci on 2008-06-09
I just receive a response from ZaReason support, they have been more than great on this matter.

Here's a preliminary walkthrough. Run these commands (don't actually type
the $ sign) one by one in a Terminal:

$ sudo apt-get install build-essential subversion
$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk uvcvideo
$ cd uvcvideo
$ gedit uvc_driver.c

Search for 0x174f in uvc_driver.c and replace the 0x5212 on the following
line with 0x5a3d and save and exit.

$ gedit Makefile

Change "INSTALL_MOD_DIR := usb/media" to "INSTALL_MOD_DIR :=
ubuntu/media/usbvideo"

$ make
$ sudo make install

Reboot and you should have it working. After a kernel update, just go to the
uvcvideo directory and redo the last two commands "make" and "sudo make
install".

=> SOLVED

---

