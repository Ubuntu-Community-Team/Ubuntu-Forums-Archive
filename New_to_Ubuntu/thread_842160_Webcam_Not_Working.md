---
title: "Webcam Not Working"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by s.fox on 2008-06-27
Hello to everybody,

I have been using Ubuntu (Hardy Heron) for just under a week now and everything is going well, however i am having difficulty with getting my webcam to work.  The webcam is detected, but programs such as skype and aMsn just show a black box as output.  I have tried to follow instructions on the web without any luck.  I don't really know many linux commands so please be patient with me.

lsusb gives me:

ashley@ashley-desktop:~$ lsusb
Bus 005 Device 003: ID 07d1:3c03 D-Link System
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 0a5c:2039 Broadcom Corp.
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 005: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 001 Device 001: ID 0000:0000

---

### Post by nothingspecial on 2008-06-27
You could see if cheese works -

```
sudo apt-get install cheese
```

Then to run it

```
cheese
```

This worked on my laptop. After I installed cheese my web cam miraculously worked with skype.

---

### Post by nothingspecial on 2008-06-27
Also have a look at this. It`s the same as yours.

[http://muhdzamri.blogspot.com/2007/03/setting-up-webcam-on-linux-zc0301.html](http://muhdzamri.blogspot.com/2007/03/setting-up-webcam-on-linux-zc0301.html)

---

### Post by peakshysteria on 2008-06-27
**This describes your cam: [http://ubuntuforums.org/showthread.php?t=703070](http://ubuntuforums.org/showthread.php?t=703070) and a solution** :) Ubuntu geek is the thing for you I think: [http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html](http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html)
And:
Have you configured Amsn via the others ---> Edit audio and video settings? And have you checked to see that Amsn's port is opened and not closed?

If this doesn't help try to change the driver:
```
sudo aptitude install subversion
svn co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
cd linux-uvc
sudo make
sudo make install
sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
sudo cp uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko
sudo modprobe uvcvideo
```

---

### Post by s.fox on 2008-06-27
Thank you all for the replies.  Sadly non of the suggestions worked,  I am still getting a black box as video output.  I was looking at the ports in aMsn and it says in red writing "You are firewalled or behind a router".   I don't know if this helps you guys but I do have the driver disc that came with my webcam.  I have been able to use this driver disc on vista with no problems.  Can ubuntu not use these drivers?

The files on the driver disc are:-
data1.cab
data1.hdr
data2.cab
engine32.cab
layout.bin
setup.boot
setup.exe
setup.ini
setup.inx

if any additional information is needed please let me know.

thanks to all who have replied to this thread.

---

### Post by s.fox on 2008-06-27
i have done a little research and found this web page which tells me that my webcam is in the non working list for skype. 

[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

Oh well.  Hopefully it will at least work in aMsn

---

### Post by s.fox on 2008-06-28
Really stuck here.  Don't know what to do.  Can anyone please help me?

---

### Post by Methuselah on 2008-06-28
Do you know if your webcam is supported under linux?
Not all are.

If it is UVC (USB Video Class) compliant it should work because they have a standard communication protocol and linux has a uvc driver. Otehrwise, unless there is a driver specific to your device out there, there is probably no easy way to get it to work.

Try this page to see if the cam is UVC compliant:

[http://www.quickcamteam.net/documentation/faq/how-do-i-find-out-whether-my-camera-is-a-uvc-device-or-not](http://www.quickcamteam.net/documentation/faq/how-do-i-find-out-whether-my-camera-is-a-uvc-device-or-not)

---

### Post by Methuselah on 2008-06-28
OK, it seems it isn't UVC compliant but might work with the spca5xx chipset driver:

See:
[http://www.linuxlaptopwiki.net/wiki/Z-Star_Corp_ZC0301_WebCam](http://www.linuxlaptopwiki.net/wiki/Z-Star_Corp_ZC0301_WebCam)

This link might also be valuable to you:

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

Basically try:

```

sudo modprobe gspca

```

If all goes well, it should attach to your plugged in camera and create a v4l device node for skype et al.
After that I think you can create a 'gspca' entry in /etc/modules to load it automatically at boot.
Otherwise, you'll always have to issue the above command prior to using the camera.

---

### Post by s.fox on 2008-06-28
Thank you for the advice Methuselah
I ran sudo modprobe gspca and got
```
ashley@ashley-desktop:~$ sudo modprobe gspca
ashley@ashley-desktop:~$ 
```

is that all you would expect to see?   i did see if it fixed my webcam but i am still getting a black box in skype and aMsn.

---

### Post by loell on 2008-06-28
this webcam uses the gspca driver already, but seems to just produce a dark image?

this is a driver issue which has not been resolved yet  :(

you could try

```
$sudo -s       
echo "4" > /sys/module/gspca/parameters/gamma 
echo "240" > /sys/module/gspca/parameters/GRed

```

to change the gamma.

---

### Post by Methuselah on 2008-06-28
Yeah, it doesn't really say anything after loading modules.

```

lsmod | grep gspca

```

Should show the module though.

I would also actually quit skype (really quite so it doesn't appear in tray) and reopen to test.
Go to the skype video options and tell me what you see under select webcam.
If your webcam was detected you should be able to select it from the dropdown, click apply then test and see video.

I don't have your type of cam so I'm not sure exactly how it behaves under linux.

---

### Post by s.fox on 2008-06-28
thanks for all the replies.  sadly still not working :(

```
ashley@ashley-desktop:~$ lsmod | grep gspca
gspca                 643920  0 
videodev               29440  1 gspca
usbcore               146028  9 zd1211rw,prism2_usb,rt73usb,rt2x00usb,hci_usb,gspca,ehci_hcd,uhci_hcd
ashley@ashley-desktop:~$ 

```

The webcam selections in skype says "Z-star vlmicro zco301p (/dev/video0)

Also i tried the code bellow but terminal just hung doing nothing at all.  THat can't be right can it?

```
$sudo -s       
echo "4" > /sys/module/gspca/parameters/gamma 
echo "240" > /sys/module/gspca/parameters/GRed
```

---

### Post by loell on 2008-06-28
it shouldn't give an output so its just fine,

now try your webcam again, if theres any changes.

---

### Post by s.fox on 2008-06-28
Sorry, no changes.

---

### Post by Methuselah on 2008-06-28
Looks like there are issues with support for your webcam.
If the driver attaches to it and it is selected in skype it should work IMO.

UVC compliant webcams are a better bet.
I know that is little solace if the one you have is built into your device.

Maybe someone else, probably someone with this camera has some other ideas that could help.

---

### Post by s.fox on 2008-06-28
Well thank you for your help anyway Methuselah.  Kinda annoying that the cam works in Vista though.   i am sure i can't be the only person who has this webcam and runs linux.

---

### Post by s.fox on 2008-06-28
Does anybody have this webcam?  Did you manage to get it working?

---

### Post by s.fox on 2008-06-30
Think i am going to give up with getting this webcam to work. :(

Can anybody suggest a webcam to get that will work without me having to mess around with drivers and stuff?  I have a budget of around £20. 

Thanks to everyone for trying to help me.

---

### Post by loell on 2008-06-30
imho, go with **logitech** webcam brand..

---

### Post by s.fox on 2008-07-22
Hi again everyone,

I have been given an old webcam from work that we were going to throw away.  I thought i would try this one first before i go out and by a new camera.  Unfortunately this one doesn't seem to work either.  Does anyone have any ideas about how to get this camera to work? Just thinks its a waste to spend money for no reason :)


This the chip set it uses.
```
Bus 001 Device 005: ID 0c45:613e Microdia 
```

Cheese just gives me something like a test signal picture you get on television.  Skype detects that webcam is plugged in put doesn't give a preview of the image when i click the test button.

Thanks for all the help.

---

### Post by kishanbhat on 2009-10-22
I tried this and my webcam worked:

**1. Install latest gspca**
 - Get it from [http://linuxtv.org/hg/~jfrancois/gspca/]("http://linuxtv.org/hg/%7Ejfrancois/gspca/")
 - unzip the gspca package, then untar it
 - Open terminal, cd into this directory
 - run ./configure, then run make, then run make install

**2. Install Video for Linux Control Panel**
 - get it from [http://www.debian-multimedia.org/pool/main/v/v4l2ucp/v4l2ucp_1.2-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/v/v4l2ucp/v4l2ucp_1.2-0.1_i386.deb)
 - Install this by double clicking on it!
 - Open terminal, run "gstreamer-properties"
 - set Video > Input to "Video for Linux 2" and click test to see a screen (Atleast a dark one)
 - Open terminal, run "v4l2ucp"
 - adjust brightness, contrast, gamma, etc

You are ready to go, start skype to test webcam is working!

---

### Post by aneeshjoseph@gmail.com on 2010-06-23
Thanks... It worked me too. Pretty good

---

