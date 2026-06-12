---
title: "Logitech C270 webcam install."
date: 2012-05-14
forum: New to Ubuntu
---

### Post by mliber on 2012-05-14
How do I install? In Ubuntu 12.04. Driving me nuts!
Thanx anybody!

---

### Post by nhasian on 2012-05-14
first see if its detected by the computer with:

```
lsusb
```

if it is, then see if its working by installing cheese:

```
sudo apt-get install cheese
```

---

### Post by Tom Hancox on 2012-05-15
Hello I would like to install a Logitech c210 cam. Can anyone guide me through that?

---

### Post by HunterDX77M on 2012-05-15
I just went to the Logitech site and it explicitly says the C270 doesn't support Linux:

[http://logitech-en-amr.custhelp.com/app/answers/detail/a_id/17665/related/1]("http://logitech-en-amr.custhelp.com/app/answers/detail/a_id/17665/related/1")

Sorry about that. I was looking for decent Linux compatible camera too.

---

### Post by llamabr on 2012-05-15
> **HunterDX77M said:**
> I just went to the Logitech site and it explicitly says the C270 doesn't support Linux:


That logitech does not support linux, does not entail that linux does not support logitech cameras.

To the OP: follow the first bit of advice, run cheese from cli, and paste any error output.

---

### Post by HunterDX77M on 2012-05-15
> **llamabr said:**
> That logitech does not support linux, does not entail that linux does not support logitech cameras.

True. I suppose that was a logical fallacy on my part.

---

### Post by Pablo W on 2012-07-23
Hi you all,
I reckon this is an old post, but still... 

I'm looking for a good webcam to be used in an old PC running Lubuntu 12.04 and I'm tempted to buy a C270. I wonder if you could eventually make it work in Ubuntu, despite the Logitech disclaimer.

Thanks for your feedback.
Cheers.

---

### Post by shoguevara on 2012-07-31
Hi, everybody! My c270 works out-of-the-box in Ubuntu 12.04 x64.
Didn't test the sound yet, but the pic is definitely there. Tested with Skype and cheese.

---

### Post by Pablo W on 2012-07-31
> **shoguevara said:**
> Hi, everybody! My c270 works out-of-the-box in Ubuntu 12.04 x64.
Didn't test the sound yet, but the pic is definitely there. Tested with Skype and cheese.

Thanks for your feedback, shoguevara. It would be great to hear again from you in case you test sound too.

Cheers.

---

### Post by OpenMinded on 2012-08-07
Skype audio works according to this:
[http://www.goodbyemicrosoft.net/news.php?item.674.2](http://www.goodbyemicrosoft.net/news.php?item.674.2)
I like the domain name :)

---

### Post by d4m1r on 2012-08-07
Yes, I have this model too specifically and it worked out of the box...Video + audio quality is very good too!

---

### Post by MrGoodguy69 on 2012-09-21
Try installing Chrome browser for Ubuntu 12.04 should work out of the box, sound as well. Don't bother trying to use it on Firefox or Chromium as it won't work.If you have sound issues use PulseAudio.

---

### Post by d4m1r on 2012-09-21
> **MrGoodguy69 said:**
> Try installing Chrome browser for Ubuntu 12.04 should work out of the box, sound as well. Don't bother trying to use it on Firefox or Chromium as it won't work.If you have sound issues use PulseAudio.

Works perfectly fine with both Firefox and Chromium...I would support either of those rather than closed source Chrome...

---

### Post by firekage on 2012-09-21
> **d4m1r said:**
> Works perfectly fine with both Firefox and Chromium...I would support either of those rather than closed source Chrome...

Can you tell me what you did in order to work with firefox? Are there some plugins for webcam in order to work with web browser or what?

---

### Post by d4m1r on 2012-09-21
Are both your video and audio feeds from your webcam not working? What version of Firefox are you using?

My first recommendation would be to get Cheese, which is a webcam program available for free in the Software Centre and see if your webcam works with it.

---

### Post by sashko_s on 2012-10-02
[https://help.ubuntu.com/community/Webcam#See%20also](https://help.ubuntu.com/community/Webcam#See%20also)

---

### Post by sandyd on 2012-10-02
**Necromancy - thread closed**

As per the [Ubuntu Forums code of conduct]("http://ubuntuforums.org/index.php?page=policy"), please do not post in threads more than one year old

Thanks!

---

### Post by nortexoid on 2013-01-03
I just bought this webcam and I'm using it on my Kubuntu 12.10 machine. I had to set the device preference order in Multimedia settings (both for audio and video, moving the webcam to the top), restart, and it worked. Not sure if the restart was necessary, but it didn't work initially in Skype until I restarted.

Video and audio quality are great. Skype says the C270 is one of the supported HD (720p) webcams, but I'm not sure if that's true for linux, or just Windows or Windows and Mac. Anyone? (I can't tell if the video is streaming 720p or not though Skype.)

---

### Post by dannyboy79 on 2013-01-03
i just picked up 2 c260's refurbished from newegg, they are 720p webcam's, guess it's just like the c270 but older. going to be testing very soon with it. i am using 12.04 xubuntu 64 bit on my desktop and also have a laptop sony vaio running 12.04 ubuntu with gnome classic 32bit i'll be trying it on also.

---

### Post by ojimenezo on 2013-05-02
I just get the c270 yesterday and it worked out-the box, i have ubuntu quantal 12.10 just plugged the USB and opened cheese, even worked on skype and it works amazing, fluid, nitid and smooth, its a great camera for a really nice price :)

---

### Post by ax8Zd0k on 2013-07-06
I just wanted to add for those Googling that I just bought a Logitech C270 from Best Buy (July 2013) and I connected it to a Lenovo Twist running Fedora 18 64-bit with KDE and everything worked right out of the box (I used "Cheese" to test). I also tested it with Skype on Linux and it worked too.

---

### Post by el_gallo_azul on 2013-10-26
I installed my Logitech C270 about 10 minutes ago in Ubuntu 13.04. It didn't work at first, so I unplugged the USB plug and plugged it back in, then it worked.

On Ubuntu 13.04, the device is called:
**ID 046d:0825 Logitech, Inc. Webcam C270** when I use the command 'lsusb' in the terminal
**UVC Camera (046d:0825) (PTLIB/V4L2)** in Ekiga
**UVC Camera (046d:0825) (/dev/video0**) in Skype.

I haven't downloaded anything additional, so it must work with the drivers built into Ubuntu 13.04.

---

### Post by dbkjohnstone on 2013-12-01
I have a Logitech C270 and Ubuntu 12.04 (or it may be later, since I have installed all the updates).  The C270 is a great little camera and works 'out of the box' with Ubuntu - except when it doesn't!  The system 'derecognizes' the webcam from time to time and the only solution I have found is to reboot over and over again until it recognizes it again.  I have found that when I get the message 'unable to recognize USB device...' at boot up then it hasn't recognized it (except when it has!).  Usually when this happens, the system will hang when I shut down until I physically unplug the webcam.  FYI this isn't a hardware problem because I have tried the C270 on another computer and it works fine.  Please, please will somebody tell me how to fix this!

---

### Post by Marcos_Hirano on 2014-04-17
Cheese worked smoothly. I'm using Lubuntu 13. Thanks.

---

### Post by Stu_Stone on 2014-04-28
This tip worked great for me. Thanks!

---

### Post by adiego73 on 2014-08-12
[SIZE=2][FONT=trebuchet ms]Hi there![/FONT]
[FONT=trebuchet ms]I've just bought a C270 camera, and it works fine when it is connected to USB 2.0 port, but when I plug it into USB 3.0 it doesn't.[/FONT]
[FONT=trebuchet ms]When I plug it to the USB3 Ubuntu recognizes the camera, but when I start Cheese and select it, the camera hangs up.[/FONT]

[FONT=trebuchet ms]I don't know if the camera doesn't support usb3, or if I&#8217;m doing something wrong, or If something&#8217;s disabled on my system..[/FONT]

[FONT=trebuchet ms]I am using Ubuntu 12.04 in an ASUS Zenbook UX31E.[/FONT]

[FONT=trebuchet ms]dmesg response when I connect the camera:[/FONT]

```

[FONT=trebuchet ms]diego@R2D2:~$ dmesg [/FONT]
[FONT=trebuchet ms][ 7118.773254] usb 2-1: new high-speed USB device number 2 using xhci_hcd[/FONT]
[FONT=trebuchet ms][ 7119.009928] usb 2-1: New USB device found, idVendor=046d, idProduct=0825[/FONT]
[FONT=trebuchet ms][ 7119.009939] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=2[/FONT]
[FONT=trebuchet ms][ 7119.009945] usb 2-1: SerialNumber: B5352580[/FONT]
[FONT=trebuchet ms][ 7119.010950] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)[/FONT]
[FONT=trebuchet ms][ 7119.101824] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1c.3/0000:03:00.0/usb2/2-1/2-1:1.0/input/input11[/FONT]
[FONT=trebuchet ms][ 7119.511622] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).[/FONT]
[FONT=trebuchet ms][ 7119.811946] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).[/FONT]
[FONT=trebuchet ms][ 7120.111809] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).[/FONT]
[FONT=trebuchet ms][ 7120.412306] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).[/FONT]
[FONT=trebuchet ms][ 7120.535869] set resolution quirk: cval->res = 384[/FONT]
[FONT=trebuchet ms][ 7120.536394] usbcore: registered new interface driver snd-usb-audio[/FONT]

```

[FONT=trebuchet ms]lsusb:[/FONT]

```
[FONT=trebuchet ms]diego@R2D2:~$ lsusb[/FONT]
[FONT=trebuchet ms]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT]
[FONT=trebuchet ms]Bus 002 Device 003: ID 046d:0825 Logitech, Inc. Webcam C270[/FONT]
[FONT=trebuchet ms]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=trebuchet ms]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=trebuchet ms]Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=trebuchet ms]Bus 001 Device 003: ID 064e:f300 Suyin Corp. [/FONT]
[FONT=trebuchet ms]Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. [/FONT]

```

[FONT=trebuchet ms]usb-devices:[/FONT]


```
[FONT=trebuchet ms]diego@R2D2:~$ usb-devices [/FONT]


[FONT=trebuchet ms]T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2[/FONT]
[FONT=trebuchet ms]D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1[/FONT]
[FONT=trebuchet ms]P:  Vendor=1d6b ProdID=0002 Rev=03.11[/FONT]
[FONT=trebuchet ms]S:  Manufacturer=Linux 3.11.0-031100rc6-generic ehci_hcd[/FONT]
[FONT=trebuchet ms]S:  Product=EHCI Host Controller[/FONT]
[FONT=trebuchet ms]S:  SerialNumber=0000:00:1d.0[/FONT]
[FONT=trebuchet ms]C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA[/FONT]
[FONT=trebuchet ms]I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub[/FONT]


[FONT=trebuchet ms]T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8[/FONT]
[FONT=trebuchet ms]D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1[/FONT]
[FONT=trebuchet ms]P:  Vendor=8087 ProdID=0024 Rev=00.00[/FONT]
[FONT=trebuchet ms]C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA[/FONT]
[FONT=trebuchet ms]I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub[/FONT]


[FONT=trebuchet ms]T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  3 Spd=480 MxCh= 0[/FONT]
[FONT=trebuchet ms]D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1[/FONT]
[FONT=trebuchet ms]P:  Vendor=064e ProdID=f300 Rev=02.17[/FONT]
[FONT=trebuchet ms]S:  Manufacturer=SuYin[/FONT]
[FONT=trebuchet ms]S:  Product=USB 2.0 UVC 0.3M Webcam[/FONT]
[FONT=trebuchet ms]S:  SerialNumber=HF031B-J13C-SE02-VS-R02.01.07[/FONT]
[FONT=trebuchet ms]C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=150mA[/FONT]
[FONT=trebuchet ms]I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo[/FONT]
[FONT=trebuchet ms]I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo[/FONT]


[FONT=trebuchet ms]T:  Bus=01 Lev=02 Prnt=02 Port=06 Cnt=02 Dev#=  4 Spd=480 MxCh= 0[/FONT]
[FONT=trebuchet ms]D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1[/FONT]
[FONT=trebuchet ms]P:  Vendor=0bda ProdID=0139 Rev=39.60[/FONT]
[FONT=trebuchet ms]S:  Manufacturer=Generic[/FONT]
[FONT=trebuchet ms]S:  Product=USB2.0-CRW[/FONT]
[FONT=trebuchet ms]S:  SerialNumber=20100201396000000[/FONT]
[FONT=trebuchet ms]C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA[/FONT]
[FONT=trebuchet ms]I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=06 Prot=50 Driver=rts5139[/FONT]


[FONT=trebuchet ms]T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2[/FONT]
[FONT=trebuchet ms]D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1[/FONT]
[FONT=trebuchet ms]P:  Vendor=1d6b ProdID=0002 Rev=03.11[/FONT]
[FONT=trebuchet ms]S:  Manufacturer=Linux 3.11.0-031100rc6-generic xhci_hcd[/FONT]
[FONT=trebuchet ms]S:  Product=xHCI Host Controller[/FONT]
[FONT=trebuchet ms]S:  SerialNumber=0000:03:00.0[/FONT]
[FONT=trebuchet ms]C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA[/FONT]
[FONT=trebuchet ms]I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub[/FONT]


[B]T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=046d ProdID=0825 Rev=00.12
S:  SerialNumber=B5352580
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio[/B]


[FONT=trebuchet ms]T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2[/FONT]
[FONT=trebuchet ms]D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1[/FONT]
[FONT=trebuchet ms]P:  Vendor=1d6b ProdID=0003 Rev=03.11[/FONT]
[FONT=trebuchet ms]S:  Manufacturer=Linux 3.11.0-031100rc6-generic xhci_hcd[/FONT]
[FONT=trebuchet ms]S:  Product=xHCI Host Controller[/FONT]
[FONT=trebuchet ms]S:  SerialNumber=0000:03:00.0[/FONT]
[FONT=trebuchet ms]C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA[/FONT]
[FONT=trebuchet ms]I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub[/FONT]


```

[FONT=trebuchet ms]Hope someone can help me [/FONT]:)

[FONT=trebuchet ms]Thanks in advance, and sorry my english [/FONT]:)

[FONT=trebuchet ms]Diego.[/FONT]

_**EDIT:**_

[FONT=trebuchet ms]I've recently updated the kernel version to 3.14.17 ([/FONT][https://github.com/pwr/Solaar/issues/153](https://github.com/pwr/Solaar/issues/153)[FONT=trebuchet ms]). When I connect the camera to the usb3 port, dmesg says: [/FONT]

```


[FONT=trebuchet ms][  931.037871] usb 2-1: new high-speed USB device number 5 using xhci_hcd[/FONT]
[FONT=trebuchet ms][  931.439632] usb 2-1: New USB device found, idVendor=046d, idProduct=0825[/FONT]
[FONT=trebuchet ms][  931.439644] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=2[/FONT]
[FONT=trebuchet ms][  931.439650] usb 2-1: SerialNumber: 65745460[/FONT]
[FONT=trebuchet ms][  931.440623] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)[/FONT]
[FONT=trebuchet ms][  931.531079] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1c.3/0000:03:00.0/usb2/2-1/2-1:1.0/input/input22[/FONT]


```

_(same as before)_

[FONT=trebuchet ms]I've tried to use the camera using guvcview, but the video isn't fluid.. I mean, it seems the camera is working at 3 fps, but guvcview says it is working at 45/60 fps...[/FONT]
[FONT=trebuchet ms]At this point, dmesg result has a lot of "[/FONT]*[ 862.441020] xhci_hcd 0000:03:00.0: ERROR Unknown event condition, HC probably busted*[FONT=trebuchet ms]" messages, and I find out it means that the "[/FONT]*error will only print when there's a vendor-specific error code, or some other completion code that the xHCI driver doesn't understand*[FONT=trebuchet ms]" ([/FONT][http://www.spinics.net/lists/linux-usb/msg84324.html](http://www.spinics.net/lists/linux-usb/msg84324.html)[FONT=trebuchet ms]). [/FONT]

[FONT=trebuchet ms]I've tested the camera in my work's computer (it has ubuntu 12.04 and the 3.14 kernel version, as I do), and the camera works Ok.[/FONT][/SIZE]

---

### Post by mintynz on 2014-09-11
No Problems running a C270 on a Linux Mint (17) Qiana OS. I try to setup the Logitech Software though. Using Wine it ran up the point of identifying my USB 2 port as a 1.1 on PC for some reason? So I changed it to the 3.0, made no differance to the software. Loaded Cheese, 5min later testing, Audion was off, checked in Sound preferances and changed "Recording" to the Webcam then it worked. Sweet.

---

### Post by baradrae on 2015-03-23
I ran Cheese, and this is the error message I get : 

libv4l2: error turning on stream: No space left on device


(cheese:6341): cheese-WARNING **: Could not read from resource.: gstv4l2bufferpool.c(994): gst_v4l2_buffer_pool_poll (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin18/GstV4l2Src:video_source:
poll error 1: No space left on device (28)


Can anyone help me please?

---

