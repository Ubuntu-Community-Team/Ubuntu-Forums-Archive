---
title: "Video Interface: Driver Windows Only. HELP!!"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Stoppelmonster on 2008-07-03
New at Ubuntu, and linux all together. Help me!

I have a Georgia Technologies GA-VD207.

The driver is available at: [georgia.com.tw]("http://www.georgia.com.tw/DOWNLOAD.htm")

I use HArdy Heron, Ubuntu 8.04.

I would like it to work with Ubuntu, is this possible, and how???

(^_^)

---

### Post by alienexplorers on 2008-07-03
You may be stuck running the VESA drivers since I don't think there are any Linux drivers for that card.

---

### Post by bumanie on 2008-07-03
>  	
&#12288; 	GA-VD207 USB2.0 MPEG-4 Grabber
	The USB 2.0 MPEG-4 Grabber really encode video into MPEG4 file by hardware,
	It can let you capture High-quality MPEG-1,2,4 video and audio file direct by USB 2.0 interface without sound card.
	By the way, you can create many special effects and clips video file...etc.
	Moreover sharing high-quality video file by small size to your family or friends by burning video into DVD or internet.

You should be able to find software available to do the same thing. There are plenty of encoders available in open source. If the video is coming of a camcorder and you have firewire, kino is great. Something like devede will encode just about any video codec to mpeg4. Have a search around in synaptic, google and use the search function in the forum. As far as I can tell, it just a video grabber that can then encode to mpeg4 - there are other ways of doing the same without a special piece of hardware.

---

### Post by Stoppelmonster on 2008-07-03
> **alienexplorers said:**
> You may be stuck running the VESA drivers since I don't think there are any Linux drivers for that card.

VESA, as in Video Electronics Standards Association? How do I get VESA drivers for this device?

---

### Post by Stoppelmonster on 2008-07-03
> **bumanie said:**
> As far as I can tell, it just a video grabber that can then encode to mpeg4 - there are other ways of doing the same without a special piece of hardware.

So, you are saying to jsut rid myself of the GA VD-207? Or are you saying that there are programs that I can use to control my device?

---

### Post by bumanie on 2008-07-03
Vesa is a base video driver for ubuntu that doesn't have 3d acceleration. I'm not exactly sure what you use the device for, but from the brief description of it encodes video into mpeg4 which as said, many software tools can do. What exactly do you use this device for? Are you using it as a video capture device to turn video tape into dvd?

---

### Post by Stoppelmonster on 2008-07-03
> **bumanie said:**
> Vesa is a base video driver for ubuntu that doesn't have 3d acceleration. I'm not exactly sure what you use the device for, but from the brief description of it encodes video into mpeg4 which as said, many software tools can do. What exactly do you use this device for? Are you using it as a video capture device to turn video tape into dvd?


The GA VD-207 is a video interfacing device. Connects to PC thru USB and has RCA and S-video Cable inputs. To my knowledge the devise has nothing to do with the video encoding, and only the software used to enable the device would determine video format saved. I would like to have something similar to Adobe Premier, that is what I was using when I used Windows.


When I plug in the devise I get power, but no video programs I have installed, will enable the GA VD-207 for capture.
Those programs are, KINO, Camorama, Open Movie Editor, and a few others, but they didn't work, anyhow.

---

### Post by Stoppelmonster on 2011-10-11
This issue was solved after upgrading to Ubuntu 10.4 Lucid Lynx. The generic drivers were already available and allowed the device to work properly.

---

