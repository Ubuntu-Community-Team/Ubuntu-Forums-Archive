---
title: "Skype video preview not working."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by optimusmedia on 2008-05-02
I am using Skype for Linux 2.0.0.68 with a Quickcam pro 4000.
While the person I am talking too can see my video fine, I can not see myself in the preview window or when testing video.  I get a black screen (screen shot provided).

Video preview does work in other programs, like Ekiga.

```

~$ lsmod | grep videodev
videodev               29696  1 pwc

~$ lsusb
Bus 001 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000

~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
```

Thanks in advance.

---

### Post by adpereira on 2008-06-25
I'm having the same problem, only difference I have a Logitech Notebook Deluxe. It actually used to work in Skype before (preview included), but things somehow became messed up. As far as I remember things changed after upgrading kernel to 2.26.24-19 (btw I re-ran EnvyNG to reinstall Nvidia drivers after the upgrade)

I have camorama and can preview the camera with no difficulties, tried also with aMSN and the webcam works fine. Tried uninstalling and reinstalling Skype with no success. Been googling all around for a solution to this before reinstalling whole Ubuntu Hardy.

Also:

:~$*artsdsp -m skype*
[I]Starting the process...
Skype Xv: Xv ports available: 31
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 49
Skype Xv: No suitable overlay format found[/I]

I think that this is related to the blank preview (is it?). 

Then:

:~$ *xvinfo *
[I]X-Video Extension version 2.2
screen #0
  Adaptor #0: "Xgl Generic Texture Video"
    number of ports: 32
    port base: 48
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 32, visualID 0x2e
      depth 32, visualID 0x2f
    no port attributes defined
    maximum XvImage size: 2048 x 2048
    Number of image formats: 3
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x0
        guid: 03000000-0000-0010-8000-00aa00389b71
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff [/I]

I also found googling that it should have UVUY image format installed for it to work (what's UVUY?, I feel like Ralph Wiggum, LOL). 

I'm running out of arrows, has anybody faced the same problem, is there a way to tackle this rather than installing Hardy all over again?

Thanks in advance

---

### Post by optimusmedia on 2008-07-16
Anyone?  I'm still having this issue.  Now using Skype version 2.0.0.72

---

### Post by Nikola Ristic on 2008-07-24
I had same problem, and I fixed it using this how-to:
[http://gingedas.net/?q=node/170](http://gingedas.net/?q=node/170)
and the thing was, when you do the make command it isnt working bcs it has some errors with algo_control and hardware and the thing is that you should change some lines in files that have errors, so open the files that are generating errors (ov511_core.c, and 1 more that i forgot the name) in any text editor, find the line that has error and add // infront of it (thats the double slash that means that that line will be interpreted as a comment and wont be compiled) for example:
/home/amitai/Desktop/ov511-2.32/ov511_core.c:1716: error: unknown field &#8216;algo_control&#8217; specified in initializer
if u get something like that it means that problem is in file:/home/amitai/Desktop/ov511-2.32/ov511_core.c, in line 1716 so go and add // infront of that line, do the make again, and than step by step fix all errors until the make command goes well. than continue with sudo make install, and other steps, and after u reboot 
you need to use the forceblock=1 option
type the following in a terminal

sudo rmmod ov51x-jpeg
sudo modprobe ov51x-jpeg forceblock=1

then start skype

to enable it permanently add the line

options ov51x-jpeg forceblock=1

to the file /etc/modprobe.d/options

so thats it, it works fine for me now. I hope this helps.
Niki

---

